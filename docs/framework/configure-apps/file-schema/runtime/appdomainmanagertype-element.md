---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663916"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType > öğesi
Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<appDomainManagerType >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`value`|Gerekli öznitelik. İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi görevi gören ad alanı da dahil olmak üzere türün adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi [ \<hem de AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesini belirtmeniz gerekir. Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.  
  
 Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen tür [ \<AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesi tarafından belirtilen derlemede yoksa ve işlem başlatılamazsa oluşturulur.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar. Yeni bir uygulama <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için veözelliklerinikullanın.<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
  
 Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir. (Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir <xref:System.TypeLoadException> oluşturulur.  
  
 Türünün ve ad alanının biçimi, <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği için kullanılan biçim.  
  
 Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` `AdMgrExample` derlemedeki tür olduğunu gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerAssembly > öğesi](appdomainmanagerassembly-element.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [SetAppDomainManagerType Yöntemi](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
