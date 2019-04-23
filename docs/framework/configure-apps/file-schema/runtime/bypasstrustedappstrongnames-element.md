---
title: <bypassTrustedAppStrongNames> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179146"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames > öğesi
Tanımlayıcı adları üzerinde tam güvene yüklenen derlemeleri tam güven doğrulama atlanıp atlanmayacağını belirtir <xref:System.AppDomain>.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<bypassTrustedAppStrongNames>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Tam güven derlemeleri için tanımlayıcı adlar doğrulama önler atlama özelliğini etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu özellik etkinleştirildiğinde, bir derleme yüklendiğinde güçlü adlar doğruluğu doğrulanmaz. Varsayılan, `true` değeridir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Tanımlayıcı ad imzaları tam güven derlemeleri derlemeleri tam güven içinde yüklü olduğunda doğrulanmaz <xref:System.AppDomain>. Bu varsayılandır.|  
|`false`|Tam güven derlemeleri tanımlayıcı ad imzaları, derlemeleri tam güven içinde yüklü olduğunda doğrulanır <xref:System.AppDomain>. Tanımlayıcı ad imzası yalnızca imza doğruluğu denetlenir; bir eşleşme için başka bir güçlü ad için karşılaştırılması değil.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı adlı atlama özelliği, tam güven derleme tanımlayıcı ad imzası doğrulama yükünü ortadan kaldırır.  
  
 Atlama özelliği, güçlü bir adla imzalanır ve aşağıdaki özelliklere sahip herhangi bir derleme için geçerlidir:  
  
-   Olmadan tam olarak güvenilen <xref:System.Security.Policy.StrongName> kanıt (örneğin, `MyComputer` kanıt bölge).  
  
-   Tam olarak güvenilen yüklenen <xref:System.AppDomain>.  
  
-   Bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> , söz konusu özellik <xref:System.AppDomain>.  
  
-   Gecikmeli imzalanmış değil.  
  
> [!NOTE]
>  Atlama özelliği bilgisayarda tüm uygulamalar için bir kayıt defteri anahtarını kullanarak devre dışı bırakıldıysa, bu yapılandırma dosyası ayarı bir etkisi yoktur. Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam güven derlemeleri üzerinde tanımlayıcı ad imzası doğrulama davranışını belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı bırakma](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
