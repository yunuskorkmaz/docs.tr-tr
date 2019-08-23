---
title: Windows Identity Foundation Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: fddff8428da7efad2823f068e89c6f621283183f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942677"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="07488-102">Windows Identity Foundation Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="07488-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="07488-103">Bu bölümdeki konularda, Windows Identity Foundation (WıF) yapılandırma şeması hakkında bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07488-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="07488-104">Ayrıca, bir uygulamayı Framework tarafından sunulan sınıfları kullanarak WıF kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07488-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="07488-105">Bu sınıflar, şemadaki ilgili öğeleri ele alan bölümlerde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="07488-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="07488-106">Aşağıdaki, WıF yapılandırma şeması tarafından sunulan temel XML etiketi yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07488-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="07488-107">Öznitelikler atlanır.</span><span class="sxs-lookup"><span data-stu-id="07488-107">Attributes are omitted.</span></span> <span data-ttu-id="07488-108">Vurgulanan Yorumlar şemanın ana bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="07488-108">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="07488-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="07488-109">In This Section</span></span>  
 <span data-ttu-id="07488-110">System. IdentityModel > uygulamalarda WIF seçeneklerini etkinleştirmek için yapılandırma sağlar. [ \<](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="07488-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="07488-111">[System. IdentityModel. Services >, WIF kullanarak Pasif Federasyon için yapılandırma sağlar. \<](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="07488-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="07488-112">Oturum kimlik doğrulama modülünü (SAM) ve federal kimlik doğrulama modülünü (WSFAD) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="07488-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
