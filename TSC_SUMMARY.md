# Technical Steering Committee (TSC) Summary  

The Technical Steering Committee is a group comprised of people from companies and projects backing OpenTofu. Its purpose is to have the final decision on any technical matters concerning the OpenTofu project, providing a model of governance that benefits the community as a whole, as opposed to being guided by any single company. The current members of the steering committee are:

- Igor Savchenko ([@DiscyDel](https://github.com/DicsyDel)) representing Scalr Inc.
- Marcin Wyszynski ([@marcinwyszynski](https://github.com/marcinwyszynski)) representing Spacelift Inc.
- Roger Simms ([@allofthesepeople](https://github.com/allofthesepeople)) representing Harness Inc.
- Yevgeniy Brikman ([@brikis98](https://github.com/brikis98)) representing Gruntwork, Inc.
- Omry Hay ([@omry-hay](https://github.com/omry-hay)) representing env0
- Roni Frantchi ([@roni-frantchi](https://github.com/roni-frantchi)) temporarily filling in for Omry Hay at env0

## 2023-12-11

### Attendees:

- Igor Savchenko ([@DiscyDel](https://github.com/DicsyDel))
- Marcin Wyszynski ([@marcinwyszynski](https://github.com/marcinwyszynski))
- Roger Simms ([@allofthesepeople](https://github.com/allofthesepeople))
- Roni Frantchi ([@roni-frantchi](https://github.com/roni-frantchi))
- Yevgeniy Brikman ([@brikis98](https://github.com/brikis98))

### Absent
- Omry Hay ([@omry-hay](https://github.com/omry-hay))

### Agenda

1. Changing default registry namespace to opentofu
   1. **Context**  
      The namespace default change to OpenTofu had some unintended consequences and edge cases with versioning of providers and the interaction of having both hashicorp/xyz and xyz plain in a single config. See [Issue #988](https://github.com/opentofu/opentofu/issues/988) for more details.
   1. **Discussion**
      - Marcin thought a deprecation warning is acceptable
      - @Roni thinks there’s very little upside to making this change, and a deprecation warning of any sort could scare people away for no good reason, which with counter with the original goal of brand reputation and separation.
      - Igor suggested to soften the warning - just say something about it in docs, and not as deprecation warning label in the docs, something even softer
   1. **Vote**: Should we (a) Change the namespace (b) Add a deprecation notice when using unqualified (c) Do nothing of that sort for now, and mention something in our docs in the softest way possible
   2. **Decision**: Unanimous (c)

1. Launch date of GA
   1. **Context**  
      R&D team may be ready with a GA version as soon as December 20th. Marketing advised we should wait till after the holidays (Jan 10th) for a bigger splash.
   1. **Discussion**
      - Yevgeniy asks about engineering availability during the holiday to support early launch. Response was we have an engineering site that can support that, and Marcin mentioned other sites don’t mind jumping in some OpenTofu during the holidays as well
      - Igor and Yevgeniy felt like that while marketing/journalist’s availability as well as on personnel may be lower, engineers may actually appreciate getting their hands on something earlier and start evaluating the project during the holiday
        A mitigation was brought up to separate the marketing effort from the launch date: have OpenTofu roll out as soon as whenever ready (soft launch), and have marketing do its thing whenever they think it is most impactful (probably Jan 10th)
   1. **Vote:** Should we (a) Release GA on Dec 20th if ready as soft launch and launch marketing in Jan 10th (b) Release on Dec 20th (c) Release on Jan 10th [note on all options, we expect an RC at least a week prior to GA]
   1. **Decision**: Unanimous (c)

#### RFC/Issues reviewed

1. [Issue: Allow specifying input variables as unknown in tofu plan](https://github.com/opentofu/opentofu/issues/812)
   1. **Context**: This issue describes multiple workspaces and dependencies and how suggest a way to unlock a way to make it easier to work in such cases, also mentions Terragrunt run-all and how that would help in such cases there.
   1. **Discussion**
      - Igor and Marcin felt like the TSC should be discussion either issues that describe a wider problem and vote on asking for RFCs, or vote on RFCs
      - There was a broad discussion on workspace dependencies, what role Terragrunt plays, and what parts of it should and could be ported into OpenTofu
      - Yevgeniy felt like there are many reasons to accept 1st party support of having the entire feature in OpenTofu’s core; there are also reasons on the flipside to keep a smaller core and make sure the solution can be layered.
      - There was a broad discussion on us needing to define criteria for this specific issue, how it needs to be redefined as an issue describing a problem, the TSC should then first define criteria for RFCs, and only then ask for submission of those.
      - We then ran out of time - we will resume this topic and try to come with said criteria on the next meeting


## 2023-12-05

### Attendees:
- Igor Savchenko ([@DiscyDel](https://github.com/DicsyDel))
- Marcin Wyszynski ([@marcinwyszynski](https://github.com/marcinwyszynski))
- Roger Simms ([@allofthesepeople](https://github.com/allofthesepeople))
- Roni Frantchi ([@roni-frantchi](https://github.com/roni-frantchi))

### Absent
- Yevgeniy Brikman ([@brikis98](https://github.com/brikis98))
- Omry Hay ([@omry-hay](https://github.com/omry-hay))

### Agenda

#### Decide if we are changing the default registry namespace to opentofu
Decision: Quick unanimous yes

#### RFC/Issues reviewed

1. [Issue: UI for registry](https://github.com/opentofu/opentofu/issues/964)
   - **Discussion**
      - Roni thinks it should be a priority to have some UI there, especially as with the selected brew like design there’s convenient way to know which packages are supported by OpenTofu, and as we try to build the OpenTofu brand we cannot be sending people to have a look at HTF for modules/providers and docs (and be disappointed if some are missing and not submitted yet).
      - Igor thinks it’s a defocus for the core team and would rather not prioritize it. Disclosure: He is working on a library.tf project meant to serve as Terraform/OpenTofu registry. He thinks the community will benefit from one non-associated registry that would hold both Terraform and OpenTofu as well as other IaC.
      - Roger thought a UI/docs via the CLI would be a better way to go at it
      - Marcin had no strong opinion but also thought it is not a priority
   - **Vote**: Should we prioritize any registry ui/doc solution this Q?
      - Roni: Yes
      - Everyone else: No
   - **Decision**: Not a prio right now, but as most votes actually suggested some solutions, TSC would like to see some suggested RFCs for the above options to be submitted, and then we can re-examine

2. [RFC: Client-side state encryption](https://github.com/opentofu/opentofu/issues/874)
   - **Discussion**  
     Everyone agrees it should be accepted to as a highly requested feature, differentiating feature. @Marcin Wyszynski felt this is not the long term solution he would have wanted to see (don’t store secrets in state), but more upsides to having that intermediate solution now than not)
   - **Vote**: Should this be accepted as a higher priority this Q?
      - Everyone: Yes
   - **Decision:** Accept RFC an pull up

3. [Issue: Support OpenTofu in the VS Code Language Server](https://github.com/opentofu/opentofu/issues/970)
   - **Discussion**
      - Marcin thinks at this point it’s an unnecessary duplication and the language server would work just the same for OTF/HTF
      - Roni says that even if it doesn’t, it’s just a nice to have
      - Roger and Igor no strong opinion but think it is not a priority as well
   - **Vote**: Should this issue be accepted as a higher priority this Q?
      - Everyone: No
   - **Decision**: We may accept the RFC, but not have core team follow up on it

4. [PR: Implement gunzipbase64](https://github.com/opentofu/opentofu/pull/799)
   - **Discussion**
     Everyone agrees long term we would want OpenTofu to have custom function extensions/reuse as there’s gonna be a lot of these, but seeing it is an inverse of an existing function while its counterparts also have those, we should pursue.
   - **Vote**: Should this PR be accepted?
     Everyone: Yes
   - **Decision**: Accept PR

5. [PR: Fix filesystem state backend to be fast](https://github.com/opentofu/opentofu/pull/579)
   - **Vote**: Should this PR be accepted?
   - Everyone: Yes
   - Decision: Accept PR

With that, our time’s up. We’ll convene again next week to discuss more items.

## 2023-11-02
### Attendees: 
- Igor Savchenko ([@DiscyDel](https://github.com/DicsyDel))
- Marcin Wyszynski ([@marcinwyszynski](https://github.com/marcinwyszynski))
- Roger Simms ([@allofthesepeople](https://github.com/allofthesepeople))
- Roni Frantchi ([@roni-frantchi](https://github.com/roni-frantchi))

### Absent
- Yevgeniy Brikman ([@brikis98](https://github.com/brikis98))
- Omry Hay ([@omry-hay](https://github.com/omry-hay))

### Agenda

#### Selecting an RFC for a registry solution for resolving providers/modules
1. There was a **unanimous** consensus the RFC for [Homebrew-like artifact resolution registry component](https://github.com/opentofu/opentofu/issues/741) should be picked.
1. Main drivers for the decision (each in the meeting brought at least one of the following):  
   1. To be able to keep our word of being a drop-in replacement and innovate and win over hearts and minds we wish to have our core team focus on our CLI solution and avoid maintaining a highly available mission critical SaaS
   1. We wish to tie maximize our availability by standing on the shoulders of giants (GitHub/AWS)
   1. The transparency of the solution as a git repository, which is at the core of our competitive offering
   1. Decoupling between the solution of resolving artifacts and that of serving documentation, and artifact signing, would allow each component to be built according to their own non-functional requirements such as availability, and be replaced/evolve on its own.
1. Signing keys - we will launching with an equivalent level of security to the legacy registry, but the decoupled approach leaves the door open for future enhancements.
1. It was decided to not have the core team pursue a user facing registry design (i.e documentation part) just yet
1. Next steps are: (action item [@RLRabinowitz](https://github.com/RLRabinowitz) and [@cube2222](https://github.com/cube2222))
   1. Announcing selected RFC to the community ASAP
   1. Getting deeper into implementation details such as:
      1. Scraping (or not) of existing modules/providers + keys
      1. Detailed design on key submission
      1. Detailed design on version bumps
      1. Sharing the detailed design document
      1. Define scope and approach/breakdown of tasks for core team to pursue

#### Recurring technical steering committee meetings
  1. Since we believe we may have some backlog of agenda items still, we will start with a weekly meeting, currently looking at Thursday 7:30PM CET (exact _time_ pending, action item [@allofthesepeople](https://github.com/allofthesepeople))
  1. Agenda suggestions for meeting will be posted no less than 24h in advance, if no items are posted we will cancel the meeting

#### Personnel 
1. Following a founders meeting decision to hire core team members under various pledging companies their payroll and donate time, rather than under direct foundation payroll -
   1. Spacelift already hired two **dedicated** maintainers
   1. Spacelift built a profile and hiring pipeline dedicated for the Tofu effort which will be shared with companies interested in hiring Tofu dedicated personnel 
