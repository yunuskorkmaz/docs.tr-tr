---
title: "Derleme Adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da2137a9ab979d9e610d033324a87939a9777a97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-names"></a>Derleme Adları
Bir derlemenin adı meta verilerinde depolanır ve önemli bir derlemenin kapsamına etkileyebilir ve bir uygulama tarafından kullanılıyor sahiptir. Tanımlayıcı adlı bir derleme derlemenin adı, kültür, ortak anahtar ve sürüm numarasını içeren tam bir adı vardır. Görünen adını ve yüklenen derlemeler için kullanarak elde edilebilir bu sık verilir <xref:System.Reflection.Assembly.FullName%2A> özelliği.  
  
 Çalışma zamanı derlemesi bulun ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır. Örneğin, kesin adlandırılmış bir derleme adlı `myTypes` aşağıdaki tam ada sahip:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  İşlemci mimarisi, .NET Framework sürüm 2.0 derlemeleri işlemci özgü sürümleri izin vermek için derleme kimlik eklenir. Yalnızca İşlemci mimarisi tarafından örneğin 32-bit ve 64-bit işlemci özgü sürümleri kimliği farklı bir derleme sürümlerini oluşturabilirsiniz. İşlemci mimarisi için güçlü adları gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 Bu örnekte, tam adı bildiren `myTypes` derleme bir ortak anahtar belirteci ile güçlü bir ada sahip, kültür değeri ABD İngilizcesi için sahip ve 1.0.1234.0 sürüm sayısı. Tam zamanında (JIT) anlamına gelir "MSIL" işlemci mimarisini olduğu-32 bit kod veya 64-bit işlemci ve işletim sistemine bağlı olarak kod derlenir.  
  
 Derlemedeki türleri istekleri kodu tam nitelikli derleme adı kullanmanız gerekir. Bu tam bağlama çağrılır. Yalnızca derleme adını belirtir, kısmi bağlama .NET Framework derlemelerde başvururken izin verilmez.  
  
 .NET Framework olun derlemeleri tüm derleme başvurularını da derlemenin tam adını içermelidir. Örneğin, sürüm 1.0 için System.Data .NET Framework derleme başvurusu için aşağıdakileri içerir:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Sürüm .NET Framework sürüm 1.0 ile birlikte gelen tüm .NET Framework derleme sürüm numarası karşılık geldiğini unutmayın. .NET Framework derlemeler için kültür değer her zaman dilden bağımsız olur ve ortak anahtar yukarıdaki örnekte gösterildiği gibi aynıdır.  
  
 Örneğin, bir derleme başvurusu İzleme dinleyicisi Kur için bir yapılandırma dosyası eklemek için .NET Framework derleme sistem tam adını şunlardır:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Çalışma zamanı, bir derlemeye bağlanırken derleme adları büyük küçük harf duyarsız davranır ancak her durumda bir derleme adı kullanılır korur. Birkaç araçlarında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] derleme adları büyük küçük harfe duyarlı olarak işler. Büyük küçük harfe duyarlı gibi en iyi sonuçlar için derleme adları yönetin.  
  
## <a name="naming-application-components"></a>Uygulama bileşenleri adlandırma  
 Çalışma zamanı dosya adı bir derlemenin kimlik belirlerken dikkate almaz. Derleme adı, sürüm, kültür ve güçlü ad oluşur, derleme kimliğini çalışma zamanı açık olması gerekir.  
  
 Örneğin, myAssembly.dll adlı bir derlemeye başvurur myAssembly.exe adlı bir derleme varsa, myAssembly.exe yürütüyorsa bağlama doğru oluşur. Ancak, başka bir uygulama yöntemini kullanarak myAssembly.exe yürütülürse <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, myAssembly.exe "myAssembly" bağlama istediğinde "myAssembly" zaten yüklenmiş çalışma zamanı belirler Bu durumda, myAssembly.dll hiçbir zaman yüklenir. MyAssembly.exe istenen tür içermediğinden bir <xref:System.TypeLoadException> oluşur.  
  
 Bu sorunu önlemek için uygulamayı oluşturan derlemeler değil aynı derleme adı veya farklı dizinlerde aynı ada sahip derlemeler yerleştirin emin olun.  
  
> [!NOTE]
>  Tanımlayıcı adlı bir derleme genel derleme önbelleğinde yerleştirirseniz derlemenin dosya adı (örneğin .exe veya .dll dosya adı uzantısı hariç) derleme adı eşleşmelidir. Örneğin, bir derleme dosya adı myAssembly.dll ise, derleme adı myAssembly olmalıdır. Yalnızca kök uygulama dizininde dağıtılan özel derlemeler dosya adından farklı bir derleme adı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodun Tam Adını Belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
