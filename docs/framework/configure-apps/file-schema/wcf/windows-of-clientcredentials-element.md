---
title: <windows><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940302"
---
# <a name="windows-of-clientcredentials-element"></a>\<\<ClientCredentials > öğesinin Windows >
İstemciyi temsil etmek için kullanılacak bir Windows kimlik bilgisi ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
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
|`allowedImpersonationLevel`|İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar. İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz. Geçerli değerler şunlardır:<br /><br /> İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.<br />Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.<br />Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.<br />Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.<br />Seçim Kimliğe bürünme düzeyi atanmadı.<br /><br /> Varsayılan değer kimliğidir. Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Kerberos kullanılamıyorsa kimlik doğrulamanın `true` NTLM 'ye indirgenmesini sağlamak için bu özelliği ayarlama.<br /><br /> NTLM kullanılıyorsa, bu `false` özelliğin bir özel durum oluşturması için Windows Communication Foundation (WCF) oluşmasına neden olacak şekilde ayarlanması. Bu özelliği olarak `false` ayarlamanın, NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
