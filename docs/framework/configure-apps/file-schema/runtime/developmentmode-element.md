---
title: '&lt;developmentMode&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b4eb1dfb50774cea2f7a50d5e5350b0338f41e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentMode&gt; öğesi
Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<developmentMode >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**developerInstallation**|Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|**true**|Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar.|  
|**false**|Derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramaz. Bu varsayılan değerdir|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu ayar yalnızca geliştirme sırasında kullanın. Çalışma zamanı tanımlayıcı adlı derlemeler DEVPATH bulunan sürümlerinde denetlemez. Yalnızca, bulduğu ilk derleme kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramak neden gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: DEVPATH Kullanarak Bütünleştirilmiş Kodların Konumunu Bulma](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
