---
title: <appDomainManagerAssembly> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff8c91680a0c3049fa9bc2f7e9c1bf3f654a19b9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487766"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly > öğesi
Varsayılan uygulama etki alanı işlemde uygulama etki alanı yöneticisi sağlayan derlemeyi belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<appDomainManagerAssembly >  
  
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
|`value`|Gerekli öznitelik. İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlayan derlemenin görünen adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtmeniz gerekir ve [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi. Diğer, bu öğelerden herhangi birini belirtilmezse, yoksayılır.  
  
 Varsayılan uygulama etki alanına yüklendiğinde <xref:System.TypeLoadException> belirtilen bütünleştirilmiş kodu yok veya derleme tarafından belirtilen türü içermiyor durum [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi; ve işlem başlatılamıyor. Derleme bulundu, ancak sürüm bilgisi eşleşmiyor, bir <xref:System.IO.FileLoadException> oluşturulur.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, uygulama etki alanı yöneticisi türü oluşturulan varsayılan uygulama etki alanından diğer uygulama etki alanları devralır. Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> özellikler farklı uygulama etki alanı yöneticisi türü için yeni bir uygulama etki alanı belirtin.  
  
 Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir. (Örneğin, masaüstünde çalışan bir uygulama tam güven yok.) Uygulama tam güven yoksa bir <xref:System.TypeLoadException> oluşturulur.  
  
 Derlemenin görünen adı biçimi için bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği.  
  
 Bu yapılandırma öğesi, yalnızca .NET Framework 4'teki kullanılabilir ve üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, uygulama etki alanı yöneticisi varsayılan uygulama etki alanı için bir işlem olduğunu belirtmek gösterilmektedir `MyMgr` yazın `AdMgrExample` derleme.  
  
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
- [\<appDomainManagerType > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType Yöntemi](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
