---
title: <qualifyAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4741c6a4745bdba00fdb525b39b70d0b15e005
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109454"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly > öğesi
Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.  
  
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
|`partialName`|Gerekli öznitelik.<br /><br /> Kod içinde göründüğü gibi kısmi derlemenin adını belirtir.|  
|`fullName`|Gerekli öznitelik.<br /><br /> Genel derleme önbelleğinde göründüğü şekliyle tam derleme adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kısmi derleme adları kullanarak uygulama temel dizininin derlemesinde yalnızca aramak ortak dil çalışma zamanı neden olur. Kullanım  **\<qualifyAssembly >** öğesi uygulama yapılandırma dosyanızda aramak ortak dil çalışma zamanı (adı, sürümü, ortak anahtar belirteci ve kültür) tam bütünleştirilmiş kod bilgileri sağlayın ve genel derleme önbelleğinde derleme için.  
  
 **FullName** özniteliği derleme kimliğinin dört alanı içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür. **PartialName** öznitelik, bir derlemeyi kısmen başvurmalıdır. Derlemenin metin adı (en yaygın durumda) en az belirtmeniz gerekir, ancak bu sürüm, ortak anahtar belirteci veya kültürü (veya herhangi bir birleşimini dört, ancak tüm dört) de içerebilir. **PartialName** çağrınızda belirtilen adla eşleşmelidir. Örneğin, belirtemezsiniz `"math"` olarak **partialName** yapılandırma dosyası ve çağrı özniteliğinde `Assembly.Load("math, Version=3.3.3.3")` kodunuzda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, mantıksal çağrı kapatır `Assembly.Load("math")` içine `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Kısmi derleme başvuruları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
