# Publication standard

This portfolio uses public source code and newly authored synthetic exercises. It does not publish customer cases, private repository contents, production incident artifacts or unverified performance claims.

## Evidence labels

- **Runnable lab:** code and reproducible checks exist. State exactly what was tested and the environment used.
- **Tabletop exercise:** events and decisions are fictional; no live response is implied.
- **Design exercise:** controls and tests are proposed; no deployment or operational result is implied.
- **Professional case:** use only when ownership, factual accuracy and explicit publication rights are established. Anonymization alone does not establish permission.

## Data handling

Use synthetic actors and assets. Public addresses must come from documentation ranges, loopback or other clearly identified non-operational examples. Use `example.invalid` for fictional email addresses. Do not publish real client names, internal domains, production IPs, tenant/account identifiers, screenshots of real environments, employee records, tickets, logs, database dumps, tokens, private keys, credentials or raw evidence.

Do not copy private artifacts into a public repository and try to hide only the most obvious fields. Build a fresh synthetic fixture that teaches the decision without revealing the underlying environment.

## Review before a new publication

1. Confirm the artifact is owned or licensed for the intended publication.
2. Review all new files, commit messages, links, metadata and image content manually.
3. Scan for credential patterns and operational identifiers. A clean scanner result is not proof of confidentiality.
4. Review reachable history, branches and existing artifacts if publishing a previously private repository. Changing visibility can expose all of them.
5. Verify relative links, commands and claims. Keep planned capabilities separate from implemented ones.
6. Use only supported outcome claims and identify remaining gaps.

If a credential is discovered, rotate or revoke it at the issuing service. Deleting a file or ignoring it does not invalidate the credential or remove it from history, forks or caches. Handle history cleanup separately with the repository owner.
