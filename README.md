<h1>Introduction to Declarative Web Applications </h1>

This document explains the concept of Declarative Web Applications (**DWA**) and how they can benefit web applications created by Web Designers and Content Editors, along with DWA partners, contributors, and [patrons](./PATRONS.md). 

For example, Bluescape would benefit by reducing the attack surface in authentication flows and by making it easier to embed 3rd party apps on the drawing board. A Google Web Designer and Adobe AEM would benefit by having 3rd party injectable apps as an available component when composing own and partner apps.

The DWA initiative plans to have its concepts included as a part of the World Wide Web Consortium (W3C) standards that are adhered to by web browsers. The advantages of these standards benefit adopters of the workflow even prior to their recommendation by W3C. Business development would take advantage of seamless integration of 3rd party micro applications; SFO would value smaller cost of development; Security officers would be empowered by improved security due to reduced surface of attack.

A declarative approach to web application development (without JavaScript) has advantages that are not available in a JavaScript-centric approach. The proposed solution is not meant to match all the capabilities of a browser and a programming language; it instead provides a web application development on markup level that can be used in a restricted and secure manner.

# Table of Contents
* [Benefits](#benefits)
  * [Security Considerations](#security-considerations)
  * [Performance](#performance)
        * [Adoptable transformation layers](#adoptable-transformation-layers)
  * [Developer Experience (DX) and Development Efficiency (DE)](#developer-experience-dx-and-development-efficiency-de)
* DWA Stack
  * Heritage
  * Truly Unified Resource Identifier (URI)
        * The deviation from current URI W3C definition
        * Trust and resources certification
* Declarative Custom Elements
* Page and DCE
* Module loader and mapping
* Libraries support
* Data Access Layer (DAL)
* Data Source Declaration
* Inline data island
* HTTP request
* Storage
* Data Request
* Data Response
* Consistent access to object models
* Transformation pipeline
* Data Request
* Data transformation and UI transformation pipeline
* DR & DT sharing across transformations
* Strict type check
* Semver on API
* Data Versioning with version change polyfills
* Templating
* Forms
* Form states
* Form validation
* External resources
* Form output
* Links


# Benefits
The advantages of Declarative Web Application (DWA) development for the vendor/browser implementer include extra security, performance, 
and reliability to the platform. Even if the process is not completely supported by W3C it still has many benefits to both internal and external parties. The following cases detail where it would be valuable:

* Authentication flow in custom apps (based on electron, QT, etc.)
* Site builders
* Content management systems
* Web 3.0 multi vendor app portals
* Embedded devices where memory and CPU resources are limited
* Internet of Things (IoT) management tools, especially due to backward compatibility polyfills layer.
* Highly responsive dynamic UI (like video set top box), which require reliability over extended periods of time, and minimized memory allocations and/or * * * multithreaded sub-flows

## Security Considerations

* No JavaScript as a source of cross-domain infiltration makes this development method inherently more secure.
* Permitted operations are subject to strict rules in browser runtime and discoverable by code analyzers.
* The ability to safely embed a DWA as a micro-application into a host web application, with minimal to no micro-application container code. 

## Performance

Declarative custom elements coupled with other aspects in declarative syntax lead to natively compiled multithreaded web apps.

* **Loading**: The declarative application can be initialized completely in the pipe of the source stream reader. As there is no need to pause for single-threaded JS execution, the branched threads would be served in the same fashion as usual HTML loading flow with sync on-the-need basis like during document dependencies load (css, fonts, etc.).
* **Data dependencies**: These can be treated in the same fashion as HTML document dependencies, they are synchronized with the HTML loading lifecycle and Document Object Model  (DOM) elements they are a part of. The hydration of UI with associated data would be a browser responsibility and turned on as-needed with platform specifics and runtime considerations taken into account.
* **Native multithreading**: As data dependencies within transformation are known, data transformation pipelines can be executed in parallel. Various UI components with their own data/dependencies flows can run in their own threads, synchronized only on the dependencies life cycle.
* **Binary code**: When data and events execution defined as transformation pipeline declaratively and in/out data schema is known, the next logical step is to generate the binary code.
* **SSR vs transformation pipeline caching**. Any part of the transformation pipeline is serializable and can be stored and later served to become a part of further DWA lifecycle. The whole DWA or one of transformation pipelines sub-chain can be pre-rendered on server side or in browser and cached to be reused without processing again. This process, sometimes called memoization, is applicable as for data as for UI pipelines. Unlike in classic memoization, here it would be just a hint to a system which could free associated resources as needed.

**Memory**:

* Data transformation/processing can begin on loading (for streaming applications).
* The memory would not be allocated for unused data at the moment of streamed data reading.
* Intermediate data would be disposed of immediately after delivery to the target. For example, once it is rendered into HTML.

### Adoptable transformation layers
Some environments could be performance optimized and parts of the transformation pipeline trimmed off. For example if the original messaging is in English(US), there is no need to apply localization. The support for screen readers can be triggered by the browser dynamically only when it is activated; after extensive use the unchanged server-side APIs can bypass the schema validation, and so on up to the level of bare minimum needed in a particular situation.

## Developer Experience (DX) and Development Efficiency (DE)
As many aspects of web application flow would be implemented by the platform itself, those would come out of the development scope. Examples include loading of data, filling into templates, and rendering HTML out of the template. 

**DX on Data schema change**: The schema checks against used data and allows it to highlight the missing/changed objects in the data source and track the effect of changes.

**Schema validation** becomes a part of the loading and runtime check. Dev tools would highlight the warning and error on the network access level and lead to affected behavior troubleshooting flow: the transformation parts and up to affected UI parts highlighting.

**Debugging & troubleshooting** goes to a  new level. The debugger embedded into the browser and in addition to the call stack it would provide the transparent exploring from generated DOM level via transformation up to the remote data source fields. 
The [devtools plugin](https://chrome.google.com/webstore/detail/epa-wgcustom-element/hiofgpmmkdembdogjpagmbbbmefefhbl) is now available for DCE and would adopt the hierarchy of data and transformations on the page to navigate through and debug each transformation individually.

*8The pipeline of incremental improvement** for UI would give ability to apply [AOP](https://en.wikipedia.org/wiki/Aspect-oriented_programming)
approach for feature based modular development. The layers of localization, analytics gathering, accessibility would be easier to be implemented and deployed independently. 

Going further the complimentary pipeline layers can be applied only for particular environments or user sessions. Jus as a sample,

* test IDs generated only during the end-to-end or unit tests, 
* inline translation editing for lingual team members, 
* feature flags would alter different transformation flows and finally UI. 
