---
title: "&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7698e280aeae29e11a7f1eba0137d83b3015d525
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;
Bir adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netNamedPipeBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ProtectionLevel|Adlandırılmış kanal koruma düzeyini tanımlar. İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır. Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Koruma yok.<br />-Oturum: İletileri imzalanmıştır.<br />-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.<br /><br /> Da EncryptAndSign varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
