---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 1bfa0ddbeba7546044a0d1ed15f4c2ff303b1491
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583630"
---
# <a name="specifying-an-assemblys-location"></a>Derlemenin Konumunu Belirtme
Derlemenin konumunu belirtmek için iki yolu vardır:  
  
- Kullanarak [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.  
  
- Kullanarak [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi.  
  
 Ayrıca [.NET Framework yapılandırma aracı (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) değerleme konumlarını belirtmeniz veya derlemeler için araştırma ortak dil çalışma zamanı konumlarını belirtin.  
  
## <a name="using-the-codebase-element"></a>Kullanarak \<codeBase > öğesi  
 Kullanabileceğiniz  **\<codeBase >** öğesi de derleme sürümünü yeniden yönlendirme yalnızca makine yapılandırması veya yayımcı ilkesi dosyaları. Çalışma zamanının hangi derleme sürümünün kullanılacağını belirler sürüm belirleyen dosyasından kodu temel ayarı uygulanır. Hiçbir kod tabanının belirtilirse, çalışma zamanı derlemesi için normal bir şekilde araştırmaları. Ayrıntılar için bkz [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Aşağıdaki örnek, bir derlemenin konumunu belirtmek gösterilmektedir.  
  
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
  
 **Sürüm** özniteliği için tüm Tanımlayıcı adlı derlemeler gereklidir ancak olmayan tanımlayıcı adlı derlemeler için atlanmış olabilir.  **\<CodeBase >** öğesi gerektiriyor **href** özniteliği. Sürüm aralığı belirtemezsiniz  **\<codeBase >** öğesi.  
  
> [!NOTE]
>  Tanımlayıcı adlı değil bir derleme için bir kod temel ipucu sağlayarak, ipucu uygulama temel ya da uygulama temel dizininin bir alt işaret etmelidir.  
  
## <a name="using-the-probing-element"></a>Kullanarak \<yoklama > öğesi  
 Çalışma zamanı bir kod temeli yoklama işlemi tarafından olmayan derlemeleri bulur. Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Kullanabileceğiniz [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) alt çalışma zamanı derleme bulurken arama belirtmek için uygulama yapılandırma dosyasında öğesi. Aşağıdaki örnek, çalışma zamanı araması gereken dizinleri belirt gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** özniteliği çalışma zamanı derlemeleri araması gereken dizinleri içerir. Uygulama C:\Program Files\MyApp bulunuyorsa, çalışma zamanı bir kod tabanına C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3 belirtmeyin derlemeleri arar. İçinde belirtilen dizinler **privatePath** uygulama temel dizininin alt dizinleri olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](index.md)
