---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646025"
---
# <a name="specifying-an-assemblys-location"></a>Derlemenin Konumunu Belirtme
Bir derlemenin konumunu belirtmenin iki yolu vardır:  
  
- [ \<CodeBase>](./file-schema/runtime/codebase-element.md) öğesini kullanarak.  
  
- [ \<Sondalama>](./file-schema/runtime/probing-element.md) öğesini kullanarak.  
  
 Montaj konumlarını belirtmek veya derlemeler için sondalamak için ortak dil çalışma zamanı için konumları belirtmek için [.NET Framework Configuration Tool'u (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) de kullanabilirsiniz.  
  
## <a name="using-the-codebase-element"></a>CodeBase \<> Öğesi'ni kullanma  
 ** \<CodeBase>** öğesini yalnızca makine yapılandırmasında veya derleme sürümünü yeniden yönlendiren yayımcı ilke dosyalarında kullanabilirsiniz. Çalışma zamanı hangi derleme sürümünün kullanılacağını belirlediğinde, sürümü belirleyen dosyadan kod temel ayarı uygular. Kod tabanı belirtilmezse, montaj için çalışma süresi normal şekilde sondalanır. Ayrıntılar [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'](../deployment/how-the-runtime-locates-assemblies.md)a bakın.  
  
 Aşağıdaki örnek, bir derlemenin konumunu nasıl belirtini gösterilmektedir.  
  
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
  
 **Sürüm** özniteliği tüm güçlü adlandırılmış derlemeler için gereklidir, ancak güçlü adlandırılmış olmayan derlemeler için atlanmalıdır. CodeBase>öğesi **href** özniteliğini gerektirir. ** \<** ** \<CodeBase>** öğesinde sürüm aralıklarını belirtemezsiniz.  
  
> [!NOTE]
> Güçlü adlandırılmış olmayan bir derleme için kod temel ipucu sağlıyorsanız, ipucunun uygulama tabanını veya uygulama temel dizininin bir alt dizinini işaret etmesi gerekir.  
  
## <a name="using-the-probing-element"></a>Sondalama> Öğesini \<Kullanma  
 Çalışma zamanı, sondalama yaparak kod tabanı olmayan derlemeleri bulur. Sondalama hakkında daha fazla bilgi [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../deployment/how-the-runtime-locates-assemblies.md)bakın.  
  
 Sondalama>öğesini, bir derlemeyi konumalırken çalışma zamanının araması gereken alt dizinleri belirtmek için kullanabilirsiniz. [ \<](./file-schema/runtime/probing-element.md) Aşağıdaki örnek, çalışma zamanının araması gereken dizinlerin nasıl belirtilen şekilde gösteriş yapılacağını gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **privatePath** özniteliği, çalışma zamanının derlemeleri araması gereken dizinleri içerir. Uygulama C:\Program Files\MyApp'ta bulunuyorsa, çalışma zamanı C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin ve C:\Program Files\MyApp\Bin3'te kod tabanı belirtmeyan derlemeleri arar. **privatePath'te** belirtilen dizinler, uygulama temel dizininin alt dizinleri olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)
- [Derlemelerle Programlama](../../standard/assembly/index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma](index.md)
