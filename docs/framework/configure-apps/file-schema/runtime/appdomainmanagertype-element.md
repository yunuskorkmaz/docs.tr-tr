---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154438"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType> Öğesi
Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
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
 Uygulama etki alanı yöneticisinin türünü belirtmek için, hem bu öğeyi hem de öğesini belirtmeniz gerekir [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) . Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.  
  
 Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen tür öğesi tarafından belirtilen derlemede yoksa [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) ve işlem başlatılamazsa, oluşturulur.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özelliklerini kullanın.  
  
 Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir. (Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir oluşturulur <xref:System.TypeLoadException> .  
  
 Türünün ve ad alanının biçimi, özelliği için kullanılan biçim <xref:System.Type.FullName%2A?displayProperty=nameWithType> .  
  
 Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` derlemedeki tür olduğunu gösterir `AdMgrExample` .  
  
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
- [\<appDomainManagerAssembly>Dosyalarında](appdomainmanagerassembly-element.md)
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [SetAppDomainManagerType Yöntemi](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
