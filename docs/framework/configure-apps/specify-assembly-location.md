---
title: Bir derlemeyi belirtmeyi&#39;s konumu
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 65bd075115e33486e86e8081b01b96db665e9da5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758275"
---
# <a name="specifying-an-assembly39s-location"></a>Bir derlemeyi belirtmeyi&#39;s konumu
Derlemenin konumunu belirtmek için iki yolu vardır:  
  
-   Kullanarak [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.  
  
-   Kullanarak [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi.  
  
 Aynı zamanda [.NET Framework yapılandırma aracını (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) derleme konumları belirtin veya derlemeler için araştırma ortak dil çalışma zamanı için konumlarını belirtin.  
  
## <a name="using-the-codebase-element"></a>Kullanarak \<codeBase > öğesi  
 Kullanabileceğiniz  **\<codeBase >** derleme sürümünü de yönlendiren yalnızca makine yapılandırma veya yayımcı ilke dosyaları öğesinde. Çalışma zamanı kullanmak için hangi derleme sürümü belirlediğinde, sürüm belirleyen dosyasından kod temel ayar uygulanır. Hiçbir kod temeli belirtilirse, çalışma zamanı derlemesi için normal bir şekilde araştırmaları. Ayrıntılar için bkz [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Aşağıdaki örnek derlemenin konumunu belirtme gösterir.  
  
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
  
 **Sürüm** özniteliği tüm Tanımlayıcı adlı derlemeler için gerekli değildir ancak güçlü-adlandırılmamış derlemelerde alınmamalıdır. **\<CodeBase >** öğesi gerektiriyor **href** özniteliği. Sürüm aralıklardaki belirtemezsiniz  **\<codeBase >** öğesi.  
  
> [!NOTE]
>  Tanımlayıcı adlı olmayan bir derleme için bir kod temel ipucu sağlayarak, ipucu uygulama temel veya uygulamanın ana dizin alt işaret etmelidir.  
  
## <a name="using-the-probing-element"></a>Kullanarak \<yoklama > öğesi  
 Çalışma zamanı temel bir kod yoklama tarafından yok derlemeleri bulur. Yoklama hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Kullanabileceğiniz [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) alt dizinleri çalışma zamanı bütünleştirilmiş belirlerken arama belirtmek için uygulama yapılandırma dosyasında öğesi. Aşağıdaki örnek, çalışma zamanı arayacağı dizinlerini belirt gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** özniteliği çalışma zamanı derlemeleri için arayacağı dizinleri içerir. Uygulama C:\Program Files\MyApp bulunuyorsa, çalışma zamanı kod temeli C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3 belirtmeyin derlemeleri arar. Belirtilen dizin **privatePath** uygulamanın ana dizin alt dizinleri olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [.NET Framework uygulamaları yapılandırma](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
