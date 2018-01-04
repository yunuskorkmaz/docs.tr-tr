---
title: "&lt;bypassTrustedAppStrongNames&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt; öğesi
Tanımlayıcı adlar tam güvene yüklenen tam güven derlemeleri Doğrulamayı atla belirtir <xref:System.AppDomain>.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<bypassTrustedAppStrongNames >  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Tanımlayıcı adlar tam güven derlemeler için doğrulama önler atlama özelliğini etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluğu doğrulanmaz. Varsayılan, `true` değeridir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Tam güven derlemeleri imzaları tanımlayıcı ad derlemeleri tam güvene yüklü olduğunda doğrulanmaz <xref:System.AppDomain>. Bu varsayılandır.|  
|`false`|Tam güven derlemeleri imzaları tanımlayıcı ad derlemeleri tam güvene yüklü olduğunda doğrulanma <xref:System.AppDomain>. Tanımlayıcı ad imzası yalnızca imza doğruluğu denetlenir; bir eşleşme için başka bir güçlü ad için karşılaştırıldığında değil.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı adlı atlama özelliği tam güven derlemelerin tanımlayıcı ad imzası doğrulama yükünü ortadan kaldırır.  
  
 Atlama özelliğini tanımlayıcı bir ad ile imzalanmış ve aşağıdaki özelliklere sahip herhangi bir derlemeye geçerlidir:  
  
-   Tam olarak güvenilmeyen olmadan <xref:System.Security.Policy.StrongName> kanıt (örneğin, sahip `MyComputer` bölge kanıt).  
  
-   Bir tam olarak güvenilmeyen yüklenen <xref:System.AppDomain>.  
  
-   Altında bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği, <xref:System.AppDomain>.  
  
-   Gecikme imzalı değil.  
  
> [!NOTE]
>  Atlama özelliği bilgisayardaki tüm uygulamalar için bir kayıt defteri anahtarını kullanarak kapatıldı, bu yapılandırma dosyası ayarı bir etkisi yoktur. Daha fazla bilgi için bkz: [nasıl yapılır: tanımlayıcı adlı atlama özelliğini devre dışı](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam güven derlemeleri sağlam ad imzası doğrulama davranışını belirtmek gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: Kesin Adlandırılmış Atlama Özelliğini Devre Dışı Bırakma](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
