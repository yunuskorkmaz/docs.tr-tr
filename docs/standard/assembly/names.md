---
title: Derleme adları
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733107"
---
# <a name="assembly-names"></a>Derleme adları
Bir derlemenin adı meta verilerde depolanır ve bir uygulama tarafından derlemenin kapsamı ve kullanımı üzerinde önemli bir etkisi vardır. Güçlü adlandırılmış bir derleme, derlemenin adını, kültürünü, ortak anahtarını ve sürüm numarasını içeren tam nitelikli bir ada sahiptir. Bu genellikle görüntü adı olarak adlandırılır ve yüklü derlemeler için <xref:System.Reflection.Assembly.FullName%2A> özellik kullanılarak elde edilebilir.

 Çalışma zamanı, derlemeyi bulmak ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır. Örneğin, güçlü adlandırılmış bir `myTypes` derleme aşağıdaki tam nitelikli ada sahip olabilir:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> İşlemci mimarisi, derlemelerin işlemciye özgü sürümlerine izin vermek için .NET Framework sürüm 2.0'daki derleme kimliğine eklenir. Kimliği yalnızca işlemci mimarisine göre farklılık gösterir bir derlemesürümleri oluşturabilirsiniz, örneğin 32 bit ve 64 bit işlemciye özgü sürümler. Güçlü adlar için işlemci mimarisi gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Bu örnekte, tam nitelikli ad, derlemenin `myTypes` ortak anahtar belirteci yle güçlü bir ada sahip olduğunu, ABD İngilizcesi için kültür değerine ve 1.0.1234.0 sürüm numarasına sahip olduğunu gösterir. İşlemci mimarisi "msil"dir, bu da işletim sistemine ve işlemciye bağlı olarak 32 bit kod veya 64 bit kodiçin derlenmiş tam zamanında (JIT) olacağı anlamına gelir.

 Bir derlemede türleri isteyen kod, tam nitelikli bir derleme adı kullanmalıdır. Buna tam nitelikli bağlama denir. .NET Framework'de derlemelere atıfta bulunurken yalnızca bir derleme adı belirten kısmi bağlamaya izin verilmez.

 .NET Framework'ü oluşturan derlemelere yapılan tüm derleme başvuruları da derlemenin tam nitelikli adını içermelidir. Örneğin, sürüm 1.0 için System.Data.NET Framework derlemesine yapılan bir başvuru şunları içerir:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Sürümün .NET Framework sürüm 1.0 ile gönderilen tüm .NET Framework derlemelerinin sürüm numarasına karşılık geldiğini unutmayın. .NET Framework derlemeleri için kültür değeri her zaman nötrdür ve ortak anahtar yukarıdaki örnekte gösterildiği gibi aynıdır.

 Örneğin, bir izleme dinleyicisi ayarlamak için yapılandırma dosyasına bir derleme başvurusu eklemek için, sistemin tam nitelikli adını eklersiniz .NET Framework derlemesi:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Çalışma zamanı, derlemeye bağlanırken montaj adlarını büyük/küçük harf duyarsız olarak ele alar, ancak derleme adına kullanılan her türlü servis talebikorur. Windows SDK'daki çeşitli araçlar derleme adlarını büyük/küçük harf duyarlı olarak işler. En iyi sonuçlar için, montaj adlarını büyük/küçük harf duyarlıymış gibi yönetin.

## <a name="name-application-components"></a>Ad uygulama bileşenleri
 Çalışma zamanı, bir derlemenin kimliğini belirlerken dosya adını dikkate almaz. Derleme adı, sürüm, kültür ve güçlü addan oluşan derleme kimliği, çalışma süresine açık olmalıdır.

 Örneğin, *myAssembly.exe* adlı bir derlemeniz varsa *myAssembly.dll*adlı bir derlemeye başvurursanız, *myAssembly.exe'yi*çalıştırSanız bağlama doğru gerçekleşir. Ancak, başka bir uygulama *myAssembly.exe* <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>yöntemini kullanarak myAssembly.exe yürütürse, çalışma zamanı `myAssembly` zaten yüklendi zaman *myAssembly.exe* isteklerini . `myAssembly` Bu durumda, *myAssembly.dll* hiçbir zaman yüklenmez. *myAssembly.exe* istenen türü içermediğinden, <xref:System.TypeLoadException> bir oluşur.

 Bu sorunu önlemek için, uygulamanızı oluşturan derlemelerin farklı dizinlerde aynı derleme adı veya yer derlemelerine sahip olmadığından emin olun.

> [!NOTE]
> .NET Framework'de, genel derleme önbelleğine güçlü adlandırılmış bir derleme koyarsanız, derlemenin dosya adı *,.exe* veya .dll gibi dosya adı uzantısını dahil etmekyerine derleme adıyla *eşleşmelidir.* Örneğin, bir derlemenin dosya adı *myAssembly.dll*ise, derleme `myAssembly`adı olmalıdır. Yalnızca kök uygulama dizininde dağıtılan özel derlemelerin dosya adından farklı bir derleme adı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Bir derlemenin tam nitelikli adını belirleme](find-fully-qualified-name.md)
- [Derleme oluşturma](create.md)
- [Güçlü adlandırılmış derlemeler](strong-named.md)
- [Genel montaj önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
