---
title: "&lt;developmentMode&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a77f93a0dff198821509c2c26f67caa137073ced
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
