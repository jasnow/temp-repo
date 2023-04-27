# ruby-advisory-db PR Rules Of The Road

All non-content conventions will be put into 3 buckets ("choices", "preference", "requirements") with the default **choices**. **preference** is the preferred item of the complete set of "choices". A "choice" becomes a **requirement** (should be fixed) if it is:

 * [A] checked by "spec" test,
 * [B] created by **github_advisory_sync.rb** script,
   * Example for [B] (Use of double quotes around patched_versions).
 * [C] not already present and supported in repo, or
 * [D] can be easily checked by local scripts,
   * Example of [D] (Use of local **yamllint** run - ignoring line-length warnings),
 * [E] can be easily corrected by local script(s).
   * Example for [E] (Use of comments and citations in .txt file => .yml file).


A current list of conventions follows:

## CONTEXT: Supported order of fields
 * PREFERENCE: README.md file's field order
 * CHOICES: CONTRIBUTING.md's field order, other file's field order
 * EXAMPLE(S): See these files for examples:
```
 * https://github.com/jasnow/ruby-advisory-db/blob/master/README.md
   -- GE, L, F, P, C, O, GH, U, T, DA, DE, C2, C3, U, P, R, N 
 * https://github.com/jasnow/ruby-advisory-db/blob/master/CONTRIBUTING.md
   -- GE,    F, P, C, O, GH, U, T, DA, DE, C2, C3, U, P, R
```
# AL>> Syn 2 files.

## CONTEXT: Length of lines
 * PREFERENCE: 80 characters
 * CHOICES: Any length (max found is 624 characters)
 * EXAMPLE(S): Many example below.

## CONTEXT: Type of quote characters
 * PREFERENCE: Double quotes    (785 lines ending with double quote)
 * CHOICES: Single quotes (425 lines ending with double quote)
 * EXAMPLE(S):
```
- '>= 0.18.1'
- ">= 12.25.0"
```
## CONTEXT: Field: gem
 * PREFERENCE: Probably covered by "spec" tests/no embedded spaces.
 * CHOICES: N/A
 * EXAMPLE(S): gem: unpoly-rails

## CONTEXT: Field: engine
 * PREFERENCE: Covered by "spec" tests (enumerated type: [ruby, rbx, jruby, mruby])
 * CHOICES: N/A
 * EXAMPLE(S): engine: ruby

## CONTEXT: Field: library
 * PREFERENCE: Only known use is for "rubygems"
 * CHOICES: N/A
 * EXAMPLE(S): library: rubygems

## CONTEXT: Field: framework
 * PREFERENCE: Only known use is for "rails" gems
 * CHOICES: N/A
 * EXAMPLE(S): framework: rails

## CONTEXT: Field: platform
 * PREFERENCE: Only known use is for "jruby"
 * CHOICES: N/A
 * EXAMPLE(S): platform: jruby

## CONTEXT: Field: cve
 * PREFERENCE: Probably covered by "spec" tests/single value
 * CHOICES: N/A
 * EXAMPLE(S): cve: 2023-28846

## CONTEXT: Field: osvdb
 * PREFERENCE: Probably covered by "spec" tests/single value
 * CHOICES: N/A
 * EXAMPLE(S): osvdb: 12345

## CONTEXT: Field: ghsa
 * PREFERENCE: Probably covered by "spec" tests/single value
 * CHOICES: N/A
 * EXAMPLE(S): ghsa: m875-3xf6-mf78

## CONTEXT: Field: url
 * PREFERENCE: Probably covered by "spec" tests/starts with "http"
 * CHOICES: N/A
 * EXAMPLE(S):
```
url: https://github.com/unpoly/unpoly-rails/security/advisories/GHSA-m875-3xf6-mf78
```

## CONTEXT: Field: title
 * PREFERENCE: single line
 * CHOICES: multiple lines
 * EXAMPLE(S):
```
title: unpoly-rails Denial of Service vulnerability
title: Fat Free CRM Gem for Ruby allows remote attackers to inject or
  manipulate SQL queries
```

## CONTEXT: Field: date
 * PREFERENCE: Probably covered by "spec" tests/single value
 * CHOICES: N/A
 * EXAMPLE(S): date: 2023-03-30

## CONTEXT: Field: description
 * PREFERENCE: Use of "|" follow by text on next line (653 times)
 * CHOICES: Text starts on same line as "description: tag (102 times) 
 * EXAMPLE(S):
```
description: |
  Gem that implements the [Unpoly server protocol](https://unpoly.com/up.protocol)
  checks](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-health-check.
  The [unpoly-rails](https://github.com/unpoly/unpoly-rails/) gem echoes
  the request URL
description: backup-agoddard Gem for Ruby contains a flaw in /lib/backup/cli/utility.rb
```

## CONTEXT: Field: cvss_v2
 * PREFERENCE: Probably covered by "spec" tests/single value (high score 10.0)
 * CHOICES: N/A
 * EXAMPLE(S): cvss_v2: 7.0

## CONTEXT: Field: cvss_v3
 * PREFERENCE: Probably covered by "spec" tests/single value (high score 10.0)
 * CHOICES: N/A
 * EXAMPLE(S): cvss_v3: 5.9

## CONTEXT: Field: patched_versions
 * PREFERENCE: List of version numbers prefixed by "~>", last one by ">"
 * CHOICES: single quotes, double quotes, no quotes around patched_Versions
 * EXAMPLE(S):
```
patched_versions
  - ~> 2.3.15
  - '~> 3.0.19'
  - "~> 3.1.10"
  - < 5.3.0
  - <= 4.4.0
  - 2.2.10
  - "= 1.6.0"
  - "> 0.16.0"
  - ">= 3.2.11"
```

## CONTEXT: Field: unaffected_versions
 * PREFERENCE: List of version numbers prefixed by "~>", last one by ">"
 * CHOICES: single quotes, double quotes, no quotes around patched_Versions
 * EXAMPLE(S):
```
 unaffected_versions
- ">= 1.9.3"
- '< 2.3.0'
- '>= 2.0.0.195'
- >= 2.0.2
- '>= 2.0.6'
```

## CONTEXT: Field: related:, [cve:, ghsa:, osvdb:, url:]
 * PREFERENCE: List of references, Same rules as associated field type. 
 * CHOICES: N/A
 * EXAMPLE(S):
```
related:
  cve:
    - 2013-1234567
    - 2013-1234568
  ghsa:
    - m875-3xf6-mf79
  osvdb:
    - 12345
  url:
    - https://github.com/rubysec/ruby-advisory-db/issues/123457
```

## CONTEXT: Field: notes
 * PREFERENCE: Assume same rules as "description:" field.
 * CHOICES: N/A
 * EXAMPLE(S): (real examples)
```
notes: "'~> 3.2.22.2' is found in gems/actionpack/CVE-2016-2097.yml"
notes: Newer versions are affected, but tracked in the actionview gem.
```
