---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f13b19dcd0aceac969d9639e6230ad33c6cd8d84
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971544"
---
# <a name="specifying-an-assemblys-location"></a>Derlemenin Konumunu Belirtme
Bir derlemenin konumunu belirtmek için iki yol vardır:  
  
- CodeBase > öğesini kullanma. [ \<](./file-schema/runtime/codebase-element.md)  
  
- Yoklama > öğesi kullanılıyor. [ \<](./file-schema/runtime/probing-element.md)  
  
 Derleme konumlarını belirtmek için [.NET Framework yapılandırma aracını (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) veya derlemeler için ortak dil çalışma zamanı için konum belirlemek üzere de kullanabilirsiniz.  
  
## <a name="using-the-codebase-element"></a>\<Codebase > öğesini kullanma  
 CodeBase > öğesini yalnızca derleme sürümünü yeniden yönlendiren makine yapılandırması veya yayımcı ilkesi dosyaları içinde kullanabilirsiniz.  **\<** Çalışma zamanı hangi derleme sürümünün kullanılacağını belirlediğinde, sürümü belirleyen dosyadan kod tabanı ayarını uygular. Hiçbir kod tabanı belirtilmemişse, çalışma zamanı derlemeyi normal şekilde araştırarak. Ayrıntılar için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Aşağıdaki örnek, bir derlemenin konumunun nasıl ekleneceğini gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **Sürüm** özniteliği, tanımlayıcı adlı tüm derlemeler için gereklidir, ancak tanımlayıcı olarak adlandırılmış olmayan derlemeler için atlanmalıdır. **\<CodeBase>** öğesi gerektiriyor **href** özniteliği. Kod temeli > öğesinde sürüm aralıkları  **\<** belirtemezsiniz.  
  
> [!NOTE]
> Güçlü adlandırılmış olmayan bir derleme için bir kod temel ipucu belirtirseniz, ipucu uygulama tabanına veya uygulama temel dizininin bir alt dizinine işaret etmelidir.  
  
## <a name="using-the-probing-element"></a>\<Yoklama > öğesini kullanma  
 Çalışma zamanı, yoklama ile kod tabanı olmayan derlemeler bulur. Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Bir derlemeyi bulurken çalışma zamanının aranması gereken alt dizinleri belirtmek için uygulama yapılandırma dosyasındaki [ \<yoklama >](./file-schema/runtime/probing-element.md) öğesini kullanabilirsiniz. Aşağıdaki örnek, çalışma zamanının arama gereken dizinlerin nasıl gösterileceğini gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** özniteliği, çalışma zamanının derlemeler için arama gereken dizinleri içerir. Uygulama C:\Program Files\MyApp konumunda bulunuyorsa, çalışma zamanı C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3. ' de bir kod tabanı belirtmeyen derlemeler arayacaktır **PrivatePath** içinde belirtilen dizinler, uygulama temel dizininin alt dizinleri olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](index.md)
