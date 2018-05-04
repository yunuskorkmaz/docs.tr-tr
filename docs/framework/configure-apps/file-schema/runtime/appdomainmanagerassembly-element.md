---
title: '&lt;appDomainManagerAssembly&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7656f4819e8ed6d8c1c87eabcbd5862929d47cdc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltappdomainmanagerassemblygt-element"></a>&lt;appDomainManagerAssembly&gt; öğesi
İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlar derleme belirtir.  
  
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
|`value`|Gerekli öznitelik. İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlar derleme görünen adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtin ve [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi. Bu öğelerden birini belirtilmedi, diğer göz ardı edilir.  
  
 Varsayılan uygulama etki alanı yüklendiğinde <xref:System.TypeLoadException> belirtilen derleme mevcut değilse veya derleme tarafından belirtilen tür içermiyorsa durum [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi; ve işlem başlatılamıyor. Derleme bulundu, ancak sürüm bilgilerini eşleşmiyor, bir <xref:System.IO.FileLoadException> oluşturulur.  
  
 Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türü devralır. Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> yeni bir uygulama etki alanı için farklı uygulama etki alanı yöneticisi türünü belirtmek için özellikler.  
  
 Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir. (Örneğin, tam güven masaüstünde çalışan bir uygulama vardır.) Uygulama tam güven, yoksa bir <xref:System.TypeLoadException> oluşturulur.  
  
 Derleme görünen adı biçimi için bkz: <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği.  
  
 Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olduğunu belirtmek gösterilmiştir `MyMgr` yazın `AdMgrExample` derleme.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [\<appDomainManagerType > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [SetAppDomainManagerType Yöntemi](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
