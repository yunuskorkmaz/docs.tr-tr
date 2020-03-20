---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154438"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType> Öğesi
Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
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
|`value`|Gerekli öznitelik. İşlemdeki varsayılan uygulama etki alanıiçin uygulama etki alanı yöneticisi olarak hizmet veren ad alanı da dahil olmak üzere, türün adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi hem de [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) öğesini belirtmeniz gerekir. Bu öğelerden biri belirtilmemişse, diğer insalar yoksayılır.  
  
 Varsayılan uygulama etki alanı <xref:System.TypeLoadException> yüklendiğinde, [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) öğesi tarafından belirtilen derlemede belirtilen tür yoksa atılır; ve işlem başlatılmaz.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğiniz zaman, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türünü devralır. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> Yeni bir <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özellikleri kullanın.  
  
 Uygulama etki alanı yöneticisi türünü belirtmek, uygulamanın tam güvene sahip olmasını gerektirir. (Örneğin, masaüstünde çalışan bir uygulama tam güvene sahiptir.) Uygulama tam güvene sahip değilse, bir <xref:System.TypeLoadException> atılır.  
  
 Tür ve ad alanı biçimi, özellik için kullanılan <xref:System.Type.FullName%2A?displayProperty=nameWithType> biçimle aynıdır.  
  
 Bu yapılandırma öğesi yalnızca .NET Framework 4 ve sonraki yerlerde kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir işlemin varsayılan uygulama etki alanı için uygulama `MyMgr` etki alanı `AdMgrExample` yöneticisinin derlemedeki tür olduğunu nasıl belirtilir.  
  
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
- [\<appDomainManagerAssembly> Öğesi](appdomainmanagerassembly-element.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [SetAppDomainManagerType Yöntemi](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
