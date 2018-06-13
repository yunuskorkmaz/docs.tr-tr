---
title: Windows Identity Foundation Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8e813383f68644315d59aa58f87cea7532a1d4c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767615"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="32126-102">Windows Identity Foundation Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="32126-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="32126-103">Bu bölümdeki konular, Windows Identity Foundation (WIF) yapılandırma şeması hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32126-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="32126-104">Ayrıca uygulama çerçevesi tarafından kullanıma sunulan sınıflarıyla WIF kullanmak için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32126-104">You can also configure an application to use WIF through classes exposed by the framework,.</span></span> <span data-ttu-id="32126-105">Bu sınıfların şemada ilgili öğeleri kabul bölümlerde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32126-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="32126-106">Aşağıdaki gösterildiği temel XML Yapısı WIF yapılandırma şeması tarafından kullanıma sunulan etiketleyin.</span><span class="sxs-lookup"><span data-stu-id="32126-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="32126-107">Öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="32126-107">Attributes are omitted.</span></span> <span data-ttu-id="32126-108">Vurgulanan açıklamaları şema ana bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32126-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="32126-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="32126-109">In This Section</span></span>  
 <span data-ttu-id="32126-110">[\<System.IdentityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) WIF etkinleştirmesi için sağlar yapılandırma seçenekleri uygulamalarda.</span><span class="sxs-lookup"><span data-stu-id="32126-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="32126-111">[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) WIF kullanarak pasif Federasyon sağlar yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="32126-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="32126-112">Oturum kimlik doğrulama Modülü (SAM) ve federe kimlik doğrulama Modülü (WSFAM) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="32126-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32126-113">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="32126-113">Related Sections</span></span>  
 <span data-ttu-id="32126-114">[Yapılandırma, yönetim ve Yönetimi](http://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) yapılandırmak ve WIF uygulamaları ve hizmetleri yönetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="32126-114">[Configuration, Administration, And Management](http://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) Describes how to configure and manage WIF applications and services.</span></span>
