---
title: "&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cf2740b0218286178e62262723bb060dc2d3817
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;
İstemci temsil etmek için kullanılacak bir Windows kimlik bilgileri ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
\<Windows >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|İstemci iletişim kuruyorsa kimliğe bürünme tercih sunucuya ayarlar. İstemcinin kimliğe bürünme modu sunucuda zorlanmaz. Geçerli değerler şunlardır:<br /><br /> -Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkların alabilir, ancak istemci alınamıyor.<br />-Kimliğe bürünme: Sunucu istemcinin güvenlik bağlamı yerel sistemde kimliğine bürünebilir.<br />-Temsilci: Sunucu istemcinin güvenlik bağlamı uzak sistemlere kimliğine bürünebilir.<br />-Anonim: Sunucusu taklit veya istemci kimliği.<br />-Hiçbiri: Kimliğe bürünme düzeyi atanmadı.<br /><br /> Varsayılan kimliğidir. Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Bu özelliği ayarlamak `true` Kerberos kullanılabilir değilse, NTLM olarak düşürmek için kimlik doğrulaması sağlar.<br /><br /> Bu özelliği ayarlamak `false` neden [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] NTLM kullanılırsa, bir özel durum için bir en iyi çaba yapma. Bu özelliği ayarlamak Not `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyebilir değil.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [İstemcilerinin güvenliğini sağlama](../../../../../docs/framework/wcf/securing-clients.md)  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
