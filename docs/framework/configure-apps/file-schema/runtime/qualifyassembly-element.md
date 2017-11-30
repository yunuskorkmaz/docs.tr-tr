---
title: "&lt;qualifyAssembly&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyAssembly&gt; öğesi
Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<qualifyAssembly >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`partialName`|Gerekli öznitelik.<br /><br /> Kodda göründüğü gibi derleme kısmi adını belirtir.|  
|`fullName`|Gerekli öznitelik.<br /><br /> Genel derleme önbelleğinde göründüğü gibi derlemenin tam adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> kısmi derleme adları kullanarak yöntemi uygulamanın ana dizin derlemede yalnızca aramak ortak dil çalışma zamanı neden olur. Kullanım  **\<qualifyAssembly >** aramak ortak dil çalışma zamanı neden ve tam derleme bilgileri (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak için uygulama yapılandırma dosyasında öğesi genel derleme önbelleğinde derleme için.  
  
 **FullName** özniteliği derleme kimliği dört alanları içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür. **PartialName** öznitelik, bir derlemeyi kısmen başvurmalıdır. En az derlemenin metin adı (en yaygın harf) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültür (veya dört ancak tüm dört herhangi bir birleşimini) de içerir. **PartialName** , çağrısında belirtilen adıyla eşleşmelidir. Örneğin, belirtemezsiniz `"math"` olarak **partialName** yapılandırma dosyasını ve arama özniteliğinde `Assembly.Load("math, Version=3.3.3.3")` kodunuzda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, mantıksal olarak çağrı kapatır `Assembly.Load("math")` içine `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Çalışma zamanı derlemeleri nasıl bulur](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [NIB: Kısmi derleme başvuruları](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
