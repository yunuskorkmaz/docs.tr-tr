---
title: "&lt;dependentAssembly&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a968d2d1abf6e77cddd9d0a0367822ee4f9723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependentassemblygt-element"></a>&lt;dependentAssembly&gt; öğesi
Her bir derleme için bağlama ilkesi ve derleme konumunu saklar. Kullanmayı `dependentAssembly` her derleme için öğesi.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<dependentAssembly >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyIdentity`|Derleme hakkında tanımlayıcı bilgileri içerir. Bu öğe her eklenmelidir `dependentAssembly` öğesi.|  
|`codeBase`|Çalışma zamanı bilgisayarda yüklü değilse paylaşılan bir derlemede bulabileceğiniz belirtir.|  
|`bindingRedirect`|Bir derleme sürümünü diğerine yeniden yönlendirir.|  
|`publisherPolicy`|Çalışma zamanı bu derleme için yayımcı ilkesi geçerli olup olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki derlemeler için derleme bilgileri yalıtan gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
