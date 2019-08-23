---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934679"
---
# <a name="transport-of-netnamedpipebinding"></a>\<\<NetNamedPipeBinding > aktarma >
Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<netNamedPipeBinding>  
\<bağlama >  
\<Güvenlik >  
\<Taşıma >  
  
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
|protectionLevel|Adlandırılmış kanalın koruma düzeyini tanımlar. İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır. Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar. Geçerli değerler şunlardır:<br /><br /> Seçim Koruma yok.<br />İmzalayabilirsiniz İletiler imzalanır.<br />EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.<br /><br /> Varsayılan değer EncryptAndSign ' dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-netnamedpipebinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
