---
title: Create a Communication Arrangement for Outbound Communication
description: Create a communication arrangement to connect your ABAP Environment to an external system - either SAP or third-party.
auto_validation: true
primary_tag: products>sap-cloud-platform--abap-environment
tags: [  tutorial>intermediate, topic>abap-development, products>sap-cloud-platform ]
time: 30
author_name: Julie Plummer
author_profile: https://github.com/julieplummer20
---

## Prerequisites
- You have a user in the ABAP Environment [Connect to the ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7379dbd2e1684119bc1dd28874bbbb7b.html)
- The business catalog `SAP_CORE_BC_COM` is assigned to your user
- You have opened the SAP Cloud Platform cockpit and navigated to the correct space. See [SAP Help Portal: SAP Cloud Platform Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e47748b5bb571014afedc70595804f3e.html)


## Details
### You will learn
  - How to create a communication arrangement for SAP CP Cloud Foundry Service Integration. You can then use this communication arrangement, for example to connect your ABAP Environment instance to an external API
  - How to test this arrangement by creating a specific destination pointing to an external API

  Predefined communication scenarios allow you to, for example, exchange data between an ABAP Environment instance and an external system.
  A communication arrangement specifies the metadata for a specific communication scenario, such as your host system and the authentication method. This metadata is contained in a service key.  You can then define one or more specific destinations for this arrangement.

  For more information, see:

  - [SAP Help Portal: Communication Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2e84a10c430645a88bdbfaaa23ac9ff7.html)

  - [SAP Help Portal: Using Services in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f22029f0e7404448ab65f71ff5b0804d.html)

  - [Cloud Foundry: Managing Service Keys](https://docs.cloudfoundry.org/devguide/services/service-keys.html)

For more information on SAP Cloud Platform, accounts, and environments, see [SAP Help Portal: What is SAP Cloud Platform](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/73beb06e127f4e47b849aa95344aabe1.html)

Throughout this tutorial, objects name include the suffix `XXX`. Replace this with your group number or initials.

---

[ACCORDION-BEGIN [Step 1: ](Create a Cloud Foundry destination service instance)]
1. In SAP Cloud Cockpit: Navigate to your Space (such as Dev).

    ![Image depicting step1-space](step1-space.png)

2. Choose **Service Marketplace > Destination**

    ![Image depicting step1b-service-marketplace](step1b-service-marketplace.png)

3. Choose **Instances > New Instance.**

    ![Image depicting step1c-destination-new-instance](step1c-destination-new-instance.png)

4. Accept the defaults and choose **Next > Next > Next.**

5. On the **Confirm** screen, enter an instance name and choose **Finish**.

    ![Image depicting step1d-destination-instance-name](step1d-destination-instance-name.png)

The new instance appears in the list.

![Image depicting step1e-list-of-instances](step1e-list-of-instances.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Create a new specific destination for the service instance)]

1. Choose **New Destination**:

    ![Image depicting step2a-choose-destination-service-instance](step2a-choose-destination-service-instance.png)  

2. Then enter the following (replacing **`xxx`** with your group number). Then choose **Save**:
    - Name  = `Z_CHUCKNORRIS_xxx`
    - URL = `http://api.icndb.com/jokes/random?limitTo=[nerdy]`
    - Proxy type = Internet
    - Authentication = `NoAuthentication`

    ![Image depicting step2b-destination-settings](step2b-destination-settings.png)  

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](Check the connection)]
Check the connection:

![Image depicting step2c-check-connection](step2c-check-connection.png)  

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Open the dashboard for your ABAP service instance)]
1. Go back to your space, `Dev` and choose **Service Instances >  `your_ABAP_service_instance`**.

    ![Image depicting step3a-abap-service-instance](step3a-abap-service-instance.png)

2. Choose **Open Dashboard**.

    ![Image depicting step3b-open-dashboard](step3b-open-dashboard.png)

The dashboard opens.

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Create a communication arrangement using the service key)]
1. Choose **Communication Arrangements > New**.

    ![Image depicting step3c-create-comm-arr](step3c-create-comm-arr.png)
    .
    ![Image depicting step3d-new-comm-arr](step3d-new-comm-arr.png)

2. Choose the correct communication scenario from the drop-down list, that is **`SAP_COM_0276`** (SAP CP Cloud Foundry Service Integration). These scenarios are pre-configured by SAP.

    ![Image depicting step3e-comm-scenario](step3e-comm-scenario.png)
    .
    ![Image depicting step4a-comm-scenarios-list](step4a-comm-scenarios-list.png)

3. Enter a name, generally the name you chose for your destination service instance, that is **`EXTERNAL_API_XXX`**.

4. Paste in the service key and choose **Create**.

    ![Image depicting step4b-new-comm-arr-by-service-key](step4b-new-comm-arr-by-service-key.png)

A communication arrangement is created, along with an identically-named communication system.

![Image depicting step4c-comm-arr-list](step4c-comm-arr-list.png)
.
![Image depicting step4d-comm-arr-sys](step4d-comm-arr-sys.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Test yourself)]


[VALIDATE_1]
[ACCORDION-END]
---
