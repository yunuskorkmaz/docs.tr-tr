---
title: Derleme Adları
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9e1ba7e92614eab4d94fe953e5a0ae19611604f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927974"
---
# <a name="assembly-names"></a>Derleme Adları
Bir derlemenin adı meta verilerde depolanır ve derlemenin kapsamı üzerinde önemli bir etkiye sahiptir ve bir uygulama tarafından kullanılır. Tanımlayıcı adlı bir derlemenin, derlemenin adını, kültürünü, ortak anahtarını ve sürüm numarasını içeren tam nitelikli bir adı vardır. Bu, genellikle görünen ad olarak adlandırılır ve yüklenen derlemeler için <xref:System.Reflection.Assembly.FullName%2A> özelliği kullanılarak elde edilebilir.  
  
 Çalışma zamanı, derlemeyi bulmak ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır. Örneğin, bilinen `myTypes` bir tanımlayıcı adlı derleme aşağıdaki tam ada sahip olabilir:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
> İşlemci mimarisi, derlemelerin işlemciye özgü sürümlerine izin vermek için .NET Framework sürüm 2,0 ' deki derleme kimliğine eklenir. Kimliği yalnızca işlemci mimarisine göre farklılık gösteren bir derlemenin sürümlerini oluşturabilirsiniz, örneğin, 32 bit ve 64 bit işlemciye özgü sürümler. Güçlü adlar için işlemci mimarisi gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 Bu örnekte, tam nitelikli ad, `myTypes` derlemenin ortak anahtar belirtecine sahip bir tanımlayıcı adı olduğunu, ABD İngilizcesi için kültür değerine sahip olduğunu ve 1.0.1234.0 sürüm numarasına sahip olduğunu gösterir. İşlemci mimarisi "MSIL" olduğundan, bu, işletim sistemine ve işlemciye bağlı olarak 32 bitlik koda veya 64 bit koda derlenmiş.  
  
 Bir derlemede tür isteyen kodun tam bir derleme adı kullanması gerekir. Bu, tam olarak nitelenmiş bağlama olarak adlandırılır. Yalnızca bir derleme adı belirten kısmi bağlamaya, .NET Framework Derlemeleriyle başvurulması durumunda izin verilmez.  
  
 .NET Framework oluşturan derlemelere yapılan tüm derleme başvuruları, derlemenin tam nitelikli adını da içermelidir. Örneğin, sisteme başvurmak için 1,0 sürümü için veri .NET Framework derlemesi şunları içerir:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Sürümün, .NET Framework sürüm 1,0 ile birlikte gelen tüm .NET Framework derlemelerinin sürüm numarasına karşılık geldiğini unutmayın. .NET Framework derlemeleri için kültür değeri her zaman tarafsız olur ve ortak anahtar Yukarıdaki örnekte gösterilen şekilde aynıdır.  
  
 Örneğin, bir izleme dinleyicisi ayarlamak için bir yapılandırma dosyasına bir derleme başvurusu eklemek için, sistem .NET Framework derlemesinin tam nitelikli adını dahil edersiniz:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
> Çalışma zamanı derleme adlarını bir derlemeye bağlarken büyük/küçük harfe duyarsız olarak değerlendirir, ancak bir derleme adında hangi durumun kullanıldığını korur. Windows SDK çeşitli araçlar, derleme adlarını büyük/küçük harfe duyarlı olarak işler. En iyi sonuçlar için, derleme adlarını büyük küçük harfe duyarlı olsalar gibi yönetin.  
  
## <a name="naming-application-components"></a>Uygulama bileşenlerini adlandırma  
 Çalışma zamanı, bir derlemenin kimliğini belirlerken dosya adını dikkate almaz. Derleme adı, sürüm, kültür ve tanımlayıcı adından oluşan derleme kimliğinin çalışma zamanına açık olması gerekir.  
  
 Örneğin, MyAssembly. dll adlı bir derlemeye başvuran myAssembly. exe adlı bir derlemeniz varsa, myAssembly. exe dosyasını çalıştırırsanız bağlama doğru gerçekleşir. Ancak, başka bir uygulama metodunu <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>kullanarak MyAssembly. exe ' yi çalıştırırsa, MyAssembly. exe "myAssembly" öğesine bağlamayı istediğinde, çalışma zamanı "myAssembly" öğesinin zaten yüklü olduğunu belirler. Bu durumda, myAssembly. dll hiçbir şekilde yüklenmez. MyAssembly. exe istenen türü içermediğinden, bir <xref:System.TypeLoadException> meydana gelir.  
  
 Bu sorunu önlemek için, uygulamanızı oluşturan derlemelerin aynı derleme adına sahip olmadığından ve farklı dizinlerde aynı ada sahip derlemeler içerdiğinden emin olun.  
  
> [!NOTE]
> Tanımlayıcı adlı bir derlemeyi genel derleme önbelleğine yerleştirirseniz, derlemenin dosya adı derleme adıyla eşleşmelidir (. exe veya. dll gibi dosya adı uzantısını dahil değildir). Örneğin, bir derlemenin dosya adı myAssembly. dll ise, derleme adı myAssembly olmalıdır. Yalnızca kök uygulama dizininde dağıtılan özel derlemeler, dosya adından farklı bir derleme adına sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir derlemenin tam nitelikli adını belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
