---
title: <appDomainManagerAssembly> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154439"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly> Öğesi
İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisisağlayan derlemeyi belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`value`|Gerekli öznitelik. İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemenin görüntü adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi hem de [ \<appDomainManagerType>](appdomainmanagertype-element.md) öğesini belirtmeniz gerekir. Bu öğelerden biri belirtilmemişse, diğer insalar yoksayılır.  
  
 Varsayılan uygulama etki alanı <xref:System.TypeLoadException> yüklendiğinde, belirtilen derleme yoksa veya derleme [ \<appDomainManagerType>](appdomainmanagertype-element.md) öğesi tarafından belirtilen türü içermiyorsa atılır; ve işlem başlatılmaz. Derleme bulunurancak sürüm bilgileri eşleşmiyorsa, bir <xref:System.IO.FileLoadException> atılır.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğiniz zaman, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türünü devralır. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> Yeni bir <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özellikleri kullanın.  
  
 Uygulama etki alanı yöneticisi türünü belirtmek, uygulamanın tam güvene sahip olmasını gerektirir. (Örneğin, masaüstünde çalışan bir uygulama tam güvene sahiptir.) Uygulama tam güvene sahip değilse, bir <xref:System.TypeLoadException> atılır.  
  
 Derleme görüntü adının biçimi için <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliğe bakın.  
  
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
- [\<appDomainManagerType> Öğesi](appdomainmanagertype-element.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [SetAppDomainManagerType Yöntemi](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
