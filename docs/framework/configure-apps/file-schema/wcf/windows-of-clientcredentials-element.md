---
title: <windows> ' ın <clientCredentials> öğesi
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: fb55fb9901e4c08a3c5d7662fdb3bf12a71876bb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275164"
---
# <a name="windows-of-clientcredentials-element"></a>\<Windows >, \<clientCredentials > öğesi
İstemciyi temsil etmek için kullanılacak Windows kimlik bilgisi ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<clientCredentials >  
\<Windows >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Sunucuya istemcinin iletişim kurduğu kimliğe bürünme tercihini ayarlar. İstemcinin kimliğe bürünme modu, sunucuda zorlanmaz. Geçerli değerler şunlardır:<br /><br /> -Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkları elde edebilirsiniz, ancak istemci kimliğine bürünülemedi.<br />-Kimliğe bürünme: Sunucu, istemci güvenlik bağlamı yerel sistemde bürünebilir.<br />-Temsilci: Sunucu, uzak sistemlere istemcinin güvenlik bağlamında bürünebilir.<br />-Anonim: Sunucu bürünerek veya istemci kimliği.<br />-Yok: Kimliğe bürünme düzeyi atanmadı.<br /><br /> Varsayılan kimliğidir. Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Bu özelliği ayarlamak `true` Kerberos kullanılamıyorsa için NTLM kimlik doğrulamasının sağlar.<br /><br /> Bu özelliği ayarlamak `false` bir NTLM kullanılırsa, bir özel durum için mümkün olan en iyi hale getirmek için Windows Communication Foundation (WCF) neden olur. Unutmayın, bu özelliği ayarlamak `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyemeyebilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
