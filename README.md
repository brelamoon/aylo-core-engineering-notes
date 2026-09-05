# AYLO Core Engineering Notes

AYLO Core is building persistent digital identity through original avatars, streetwear, and connected physical-digital products. This public repository documents selected implementation principles behind the current catalog experience.

## A typed avatar catalog

Large visual catalogs become difficult to maintain when image paths, prices, and product metadata live in unrelated components. AYLO Core keeps avatar records in typed generated catalogs and uses a single checkout resolver to normalize them.

Each record has a stable avatar ID, title, audience category, tier, rarity label, price source, and image path. Collection-specific catalogs remain separate, while the resolver produces one checkout-facing shape. This makes it possible to add a collection without rewriting every product card.

The important boundary is between source metadata and public behavior. A catalog entry may exist for internal review without being intended for a public campaign. Marketing, UI availability, and checkout eligibility must therefore be explicit states rather than assumptions based on the presence of a file.

Generated catalogs need automated validation for:

- duplicate IDs;
- missing assets;
- impossible or missing prices;
- broken public paths;
- records that bypass the intended publication state.

## Public catalog versus internal review

An asset existing in source control does not mean it is ready for customers. Visual teams need room to review images, metadata, and pricing before a collection becomes part of the public product.

The checkout-facing resolver, public UI, and marketing campaign should all respect the same release decision. A reliable gate verifies that the file exists, identifiers are unique, the image format is correct, pricing is intentional, and the destination page can render the item.

This separation keeps three categories clear: shipped behavior, internal review, and future roadmap.

## Official AYLO Core links

- [Live avatar catalog](https://aylo.technology/aylo-core?utm_source=github_repo&utm_medium=technical&utm_campaign=aylo_engineering_2026_09&utm_content=typed_catalog)
- [English community](https://t.me/aylocore)
- [Instagram](https://www.instagram.com/aylo.core/)

The public catalog is the source of truth for current availability. Broader identity progression and physical-digital connections remain product direction unless they are visible and testable in the released product.
