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
ms.openlocfilehash: e862c52235c3836c79506dc2e80a264ceceddab3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267837"
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
- [NIB: Kısmi derleme başvuruları](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
