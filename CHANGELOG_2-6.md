# Change Log

*This change log IS intended to assist reviewers in assessing the changes made between Codebook Version 2.5 and Version 2.6. The list has been broken into Changes to existing elements, Enumeration list enhancements (additions to internal controlled vocabularies captured as enumerations), and new content. Note that all changes are backward compatible in that an instance of Codebook Version 2.5 will validate against Version 2.6. However, changes made to improve consistency in the use of external controlled vocabularies through broader use of the element ‘concept’ resulted in a change in best practices, in particular shifting from the use of an attribute to capture the term of a controlled vocabulary to the use of a structured ‘concept’ that supports direct attribution to the external controlled vocabulary. This was needed to provide support the resolution of entries to their external controlled vocabularies.*

# Summary

Changes were made to better support:

* Consistent attributes for all content defining individuals and organizations  
* Improved ability to link access rules to specific content  
* Expanded use of typeOfXxxx to support the use of controlled vocabularies in various locations  
* Consistent use of controlled vocabularies through the element concept  
* Updated internal enumerations  
* A new DDI controlled vocabulary  
* Metadata access information  
* Use of SDTL to describe file and variable derivations 

# Changes to existing elements:

* **Item 1** identifies two elements that have been deprecated. The instructions provide an alternative approach for each. Deprecation indicates that if these elements are used other systems using DDI Codebook may not be able to interpret them correctly and, if used, should be for internal purposes only.  
* **Items 2-6** were changed to provide a consistent set of attributes for elements containing information on individuals and organizations  
* **Item 7** adds the ability to reference access rules at various levels below the variable  
* **Items 8-13** add typeOfXxxx elements (conceptType) to a number of locations  
* **Item 14** adds an attribute allowing the labeling of an IDNo as a persistent identifier  
* **Item 15** adds an attribute to specify the URN of a vocabulary item within a controlled vocabulary for the specific concept  
* **Item 16:** adds mimeType to fileType  
* **Items 17-18** change simpleTextTypes to conceptualTextTypes or conceptTypes, each of which support the use of a concept element  
* **Item 19** changes keywork and topcClas to conceptType as it now contains the same structure as a concept
* 

| **No** | **ISSUUE**  | **OBJECT** | **ADDITION** | **CHANGE** |
| :---- | :---- | :---- | :---- | :---- |
| **1** | 84 | Link ExtLink |  | Use is deprecated. Use various available othrMatType and associated references to relate an element to the related material. |
| **2** | 42, 60, 67, 75 | AuthEntry contact custodian dataCollector depositr distrbtr fundingAg othId producer participant authorizingAgency evaluator verResp  | agentIdentifier (xs:string) typeOfAgentIdentifier (xs:string) isPersistentIdentifier (xs:Boolean) | Provides consistent information on agentIdentifier, typeOfAgentIdentifier, isPersistentIdentifier, role, affiliation, and abbreviation |
| **3** | 42, 60, 67, 75 | custodian | role (xs:string) |  |
| **4** | 42, 60, 67, 75 | AuthEntry othId | abbr (xs:string) |  |
| **5** | 42, 60, 67, 75 | fundingAg | affiliation (xs:string) |  |
| **6** | 81 | origArch | affiliation (xs:string) abbr (xs:string) URI (xs:string) agentIdentifier (xs:string) typeOfAgentIdentifier (xs:string)  |  |
| **7** | 72 | catgry catStat dataItem invalrng stdCatgry sumStat valrng | access (IDREFS) | Supports the ability to reference once or more access statements from specific levels within the variable allowing finer grained distinctions |
| **8** | 49 | othrMat setAvailability | typeOfSetAvailability (conceptType) | Added the element typeOfXxxx to several complex descriptions to support the use of controlled vocabularies |
| **9** | 49 | exPostEvaluation | typeOfExPostEvaluation (conceptType) |  |
| **10** | 49 | developmentActivity | typeOfDevelopmentActivity (conceptType) |  |
| **11** | 49, 51 | Sources resource | typeOfDataSrc (conceptType) |  |
| **12** | 49 | dataAccess | typeOfDataAccess (conceptType) |  |
| **13** | 49 | codingIntruction | typeOfCodingInstruction (conceptType) |  |
| **14** | 42 | IDNo | isPersistentIdentifier (xs:boolean) | Short cut to identifying persistent identifiers without having to know the various persistent ID types |
| **15** | 79 | concept | vocabInstanceURI (xs:string) | Supports reference to a specific term in a Controlled Vocabulary allows for validation and resolution |
| **16** | 534 | fileTxt | Attribute: mimeType (xs:string) | Adds ability to designate mime type to fileTxt |
| **17** | 79, 542 | unit instrumentDevelopment collectorTraining dataProcessing stdyClas dataAppr dataChck frequenc weight actMin avlStatus respUnit updateProcedure |  | FROM extension base simpleTextType TO conceptualTextType ADDS an option for concept and txt to the existing PHRASE, FORM, and xhtml:BlkNoForm.mix to support the use of an external controlled vocabulary  |
| **18** | 79, 541, 542 | Format Software complete docStatus imputation ProcStat |  | FROM simpleTextType TO conceptType ADDS vocab, vocabURI, and vocabInstanceURI to support the use of an external controlled vocabulary |
| **19** | 79 | Keyword topcClas |  | FROM former structure TO conceptType \[no content change as conceptType is the equivalent of former structure plus vocabInstanceURI\] |

# Enumeration list enhancements

The additions reflect expansions of the representations and response domains in DDI Lifecycle version 3.3

| No | ISSUE | NEW CONTENT ADDED TO: | NEW CONTENT | CHANGE |
| :---- | :---- | :---- | :---- | :---- |
| 1 | 59 | IN qstn/responseDomain  | Add to enumeration list: geographicLocationCode geographicStructureCode scale externalCategory nominal location ranking distribution | Adds coverage of DDI Lifecycle response domains added to Version 3.3 |
| 2 | 59 | IN var/representation  | Add to enumeration list: geographicLocationCode geographicStructureCode scale | Adds coverage of DDI Lifecycle representations added to Version 3.3 |

# New Coverage

The new content covers:

* Support for a new DDI Controlled Vocabulary  
* Definition of metadata access   
* Support for use of the new DDI product SDTL

| No | JIRA ISSUE | NEW CONTENT ADDED TO: | NEW CONTENT | CHANGE |
| :---- | :---- | :---- | :---- | :---- |
| 1 | 68 | sumDscr | generalDataFormat \[0..n\] | generalDataFormat (type="concept") |
| 2 | 62 | stdyDscr | metadataAccsType \[0..n\] | metadataAccsType     extension base: baseElementType     typeOfMetadataAccs \[type="concept"\]     element: useStmt \[0..n\] \[reused from 2.5\]     element: notes \[0..n\] |
| 3a | 43 | prodStmt | language \[0..n\] | languageType     extension base: simpleTextType     attribute: typeOfLanguageCode     attribute: languageCode |
| 3b | 61 | prodStmt | license \[0..n\] | licenseType     extension base: simpleTextType     attribute: URI     attribute: type \[data | metadata\] |
| 4 | 76 | derivation | varRange \[0..n\] | varRangeType     extension base: baseElementType     attribute: start \[xs:IDREF\]     attribute: end \[xs:IDREF\] |
| 5 | 74 | fileDscr | fileDerivation \[0..1\]  | fileDerivationType     extension base: baseElementType     element:  fileCommand \[0..n\]         drvdesc \[0..1\] \[reused from 2.5\]         drvcmd \[1..n\] \[reused from 2.5\]         fileDerivationVars \[0..n\]            attribute: keep \[0..1\] \[xs:IDREFS\]            attribute: drop \[0..1\] \[xs:IDREFS\]             attribute:add \[0..1\] \[xs:IDREFS\]     attribute: sourceFiles \[xs:IDREFS\] |

# Documentation

## Field Level: 

* Action: Attribution documentation moved to complexType from element. Element documentation reformated for consistency and clarity.  
* Action: Review and update of all field level documentation, adding examples  
* Issues covered: 42, 47, 48, 50, 55, 63, 70, 71, 82  
* GitHub issues covered: 11, 12, 14, 15, 16, 17, 18, 19, 20, 22, 23, 24, 25, 26, 27, 29, 30, 31, 32, 33, 34, 35, 36, 37  
* Revisions of documentation after review of 2.6 draft: 533, 535, 539, 540, 542, 543, 544, 545, 549, 551

## High Level:

* Action: Added high level documentation covering best practices and applied use  
* Issues covered: 36, 37, 38, 40, 44, 56, 58, 69, 80, 83, 85, 548  
* Note that High Level documentation is being published as a separate document per Development and Review Processes for DDI Standards and Official Technical Documents (section 3.0)

# Issues Tabled for Future Work:

* Action: Discussion and comments entered on issues  
* Issues: 39, 52, 54, 57, 65, 66


Changes noted in issues 104, 536, 537, and 550 to correct the 2.6 draft were also made.
