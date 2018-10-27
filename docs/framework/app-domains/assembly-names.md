---
title: Derleme Adları
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6447593ba81e4512afaf2b5798fcec00b755e63c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184791"
---
# <a name="assembly-names"></a>Derleme Adları
Bir derlemenin adı meta verilerinde depolanır ve önemli bir derlemenin kapsamına etkileyebilir ve bir uygulama tarafından kullanılıyor sahiptir. Tanımlayıcı adlı bir derleme, derlemenin adı, kültür, ortak anahtarı ve sürüm numarasını içeren tam bir adı vardır. Görünen ad ve yüklenen derlemeler için kullanılarak elde edilebilir gibi bu sık adlandırılır <xref:System.Reflection.Assembly.FullName%2A> özelliği.  
  
 Çalışma zamanı, derlemeyi ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır. Örneğin, bir tanımlayıcı adlı bütünleştirilmiş kod adında `myTypes` şu tam ada sahip olabilir:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  İşlemci mimarisi derleme kimliğini .NET Framework sürüm 2.0, işlemciye özel derlemelerin sürümleri izin vermek için eklenir. Yalnızca İşlemci mimarisi tarafından örneğin 32-bit ve 64 bit işlemciye özgü sürümlerini kimliği farklı bir derleme sürümlerini yeniden oluşturabilirsiniz. İşlemci mimarisi için tanımlayıcı adlar gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 Bu örnekte, tam adı olduğunu gösterir `myTypes` derleme tanımlayıcı bir ada sahip bir ortak anahtar belirteci sahip, ABD İngilizcesi için kültür değeri varsa ve 1.0.1234.0 sürüm numarası. Just-in-time (JIT) olacağı anlamına gelir "msil" işlemci mimarisini olduğu-32-bit kod veya işletim sistemi ve işlemci bağlı olarak, 64 bit kod derlenir.  
  
 Bir bütünleştirilmiş kodundaki türler isteyen kod tam derleme adını kullanmanız gerekir. Bu, tam bağlama olarak adlandırılır. .NET Framework'teki derlemeler başvururken belirtir. yalnızca bir derleme adı, kısmi bağlamasına izin verilmez.  
  
 .NET Framework yapan derlemelerin tüm derleme başvurularını da bütünleştirilmiş kodun tam adı içermelidir. Örneğin, sürüm 1.0 için System.Data .NET Framework derlemesine başvurmak için aşağıdakileri içerir:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Sürümü, .NET Framework sürüm 1.0 ile birlikte gelen tüm .NET Framework derlemeleri sürüm numarasını karşılık geldiğini unutmayın. .NET Framework derlemeleri, kültür değeri her zaman nötr ve ortak anahtar yukarıdaki örnekte gösterildiği gibi aynıdır.  
  
 Örneğin, bir bütünleştirilmiş kod başvurusu İzleme dinleyicisi Kur için bir yapılandırma dosyası eklemek için .NET Framework derleme sisteminin tam adı şunlardır:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Çalışma zamanı derleme adları büyük küçük harf duyarsız bir bütünleştirilmiş kod bağlama sırasında işler, ancak her durumda, bir derleme adı kullanılır korur. Çeşitli araçları [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] işleyecek derleme adları büyük/küçük harfe olarak. Bunlar büyük/küçük harfe gibi davranarak en iyi sonuçlar için derleme adları yönetin.  
  
## <a name="naming-application-components"></a>Uygulama bileşenleri adlandırma  
 Çalışma zamanı dosya adı bir derlemenin kimliğinin belirlerken dikkate almaz. Derleme adı, sürüm, kültür ve tanımlayıcı ad oluşur, derleme kimliği için çalışma zamanı açık olması gerekir.  
  
 Örneğin, da myAssembly.dll adlı bir derlemeye başvuran myAssembly.exe adlı bir derleme varsa, myAssembly.exe yürütüyorsa bağlama doğru bir şekilde gerçekleşir. Ancak, myAssembly.exe yöntemi kullanarak başka bir uygulama yürütüyorsa <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, çalışma zamanı bağlama "myAssembly." myAssembly.exe istediğinde, "myAssembly" zaten yüklü olduğunu belirler. Bu durumda da myAssembly.dll hiçbir zaman yüklenir. İstenen türü myAssembly.exe içermediğinden bir <xref:System.TypeLoadException> gerçekleşir.  
  
 Bu sorunu önlemek için uygulamanızı oluşturan derlemeleri değil aynı derleme adına sahip veya farklı dizinlerde aynı ada sahip derlemeler yerleştirin emin olun.  
  
> [!NOTE]
>  Bir katı adlı derlemeyi genel derleme önbelleğine yerleştirirseniz, derlemenin dosya adı (örneğin .exe veya .dll dosya adı uzantısı dahil değil) derleme adı eşleşmelidir. Örneğin, bir derlemenin dosya adı da myAssembly.dll ise, myAssembly derleme adı olmalıdır. Özel derlemeler yalnızca kök uygulama dizininde dağıtılan dosya adından farklı bir derleme adı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Nasıl yapılır: Bir Bütünleştirilmiş Kodun Tam Adını Belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)  
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
