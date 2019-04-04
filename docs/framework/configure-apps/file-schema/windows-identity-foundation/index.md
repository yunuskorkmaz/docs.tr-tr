---
title: Windows Identity Foundation Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 9c8009b4d95e5aa2c3d9bb8a8958040127a9e628
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441196"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="52795-102">Windows Identity Foundation Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="52795-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="52795-103">Bu bölümdeki konularda, Windows Identity Foundation (WIF) yapılandırma şeması hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="52795-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="52795-104">Ayrıca, bir uygulamayı WIF sınıfları framework tarafından kullanıma sunulan aracılığıyla kullanmak için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52795-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="52795-105">Bu sınıfları, ilgili öğeleri şemada kabul bölümlerde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52795-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="52795-106">WIF yapılandırma şeması tarafından kullanıma sunulan yapısı aşağıdaki gösterildiği temel XML etiketi.</span><span class="sxs-lookup"><span data-stu-id="52795-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="52795-107">Öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="52795-107">Attributes are omitted.</span></span> <span data-ttu-id="52795-108">Vurgulanan açıklamaları şema ana bileşenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="52795-108">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="52795-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="52795-109">In This Section</span></span>  
 <span data-ttu-id="52795-110">[\<System.IdentityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) seçenekleri uygulamalarda WIF etkinleştirme yapılandırması sağlar.</span><span class="sxs-lookup"><span data-stu-id="52795-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="52795-111">[\<System.IdentityModel.Services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) WIF kullanarak pasif Federasyon yapılandırması sağlar.</span><span class="sxs-lookup"><span data-stu-id="52795-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="52795-112">Oturum kimlik doğrulama Modülü (SAM) ve şirket dışı kimlik doğrulaması Modülü (WSFAM) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="52795-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
