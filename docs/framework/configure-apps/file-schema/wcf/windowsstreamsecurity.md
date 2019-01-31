---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: aff415bb75cf719ce19fb2189cc69c2c159af6cf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281014"
---
# <a name="windowsstreamsecurity"></a>\<windowsStreamSecurity >
Özel bağlamanın Windows akış güvenliği ayarlarını belirtin.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<windowsStreamSecurity >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|protectionLevel|İleti düzeyi güvenliği tanımlar. İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır. Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar. Geçerli değerler şunlardır:<br /><br /> -Yok: Koruma yok.<br />-Oturum: İmzalı iletiler.<br />-   EncryptAndSign: İletileri imzalanacak ve şifrelenecek.<br /><br /> EncryptAndSign varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir akışa dayalı Protokolü gibi TCP ve adlandırılmış kanallar taşımalar aktarım akışı tabanlı yükseltmeyi destekler. Özellikle, WCF güvenlik yükseltmeleri sağlar. Bu aktarım güvenliği yapılandırma bu yapılandırma öğesi tarafından yanı kapsüllenir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), hangi yapılandırılabilir ve özel bağlama için eklendi  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
