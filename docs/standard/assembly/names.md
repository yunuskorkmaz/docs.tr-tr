---
title: Derleme adları
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733107"
---
# <a name="assembly-names"></a>Derleme adları
Bir derlemenin adı meta verilerde depolanır ve derlemenin kapsamı üzerinde önemli bir etkiye sahiptir ve bir uygulama tarafından kullanılır. Tanımlayıcı adlı bir derlemenin, derlemenin adını, kültürünü, ortak anahtarını ve sürüm numarasını içeren tam nitelikli bir adı vardır. Bu, genellikle görünen ad olarak adlandırılır ve yüklü derlemeler için <xref:System.Reflection.Assembly.FullName%2A> özelliği kullanılarak elde edilebilir.

 Çalışma zamanı, derlemeyi bulmak ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır. Örneğin, `myTypes` adlı tanımlayıcı adlı bir derleme aşağıdaki tam ada sahip olabilir:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> İşlemci mimarisi, derlemelerin işlemciye özgü sürümlerine izin vermek için .NET Framework sürüm 2,0 ' deki derleme kimliğine eklenir. Kimliği yalnızca işlemci mimarisine göre farklılık gösteren bir derlemenin sürümlerini oluşturabilirsiniz, örneğin, 32 bit ve 64 bit işlemciye özgü sürümler. Güçlü adlar için işlemci mimarisi gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Bu örnekte, tam ad, `myTypes` derlemesinin ortak anahtar belirteci olan bir tanımlayıcı ada sahip olduğunu, ABD Ingilizcesi için kültür değerine sahip olduğunu ve 1.0.1234.0 sürüm numarasına sahip olduğunu gösterir. İşlemci mimarisi "MSIL" olduğundan, bu, işletim sistemine ve işlemciye bağlı olarak 32 bitlik koda veya 64 bit koda derlenmiş.

 Bir derlemede tür isteyen kodun tam bir derleme adı kullanması gerekir. Bu, tam olarak nitelenmiş bağlama olarak adlandırılır. Yalnızca bir derleme adı belirten kısmi bağlamaya, .NET Framework Derlemeleriyle başvurulması durumunda izin verilmez.

 .NET Framework oluşturan derlemelere yapılan tüm derleme başvuruları, derlemenin tam nitelikli adını da içermelidir. Örneğin, 1,0 sürümü için System. Data .NET Framework derlemesine bir başvuru şunları içerir:

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

## <a name="name-application-components"></a>Uygulama bileşenlerini Adlandır
 Çalışma zamanı, bir derlemenin kimliğini belirlerken dosya adını dikkate almaz. Derleme adı, sürüm, kültür ve tanımlayıcı adından oluşan derleme kimliğinin çalışma zamanına açık olması gerekir.

 Örneğin, MyAssembly. *DLL*adlı bir derlemeye başvuran *MyAssembly. exe* adlı bir derlemeniz varsa, *MyAssembly. exe dosyasını*çalıştırırsanız bağlama doğru gerçekleşir. Ancak, başka bir uygulama *MyAssembly. exe* ' yi Yöntem <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>kullanarak çalıştırırsa, *myassembly. exe* `myAssembly`'e bağlamayı istediğinde, `myAssembly` zaten yüklendiğini belirler. Bu durumda, *MyAssembly. dll* hiçbir şekilde yüklenmez. *MyAssembly. exe* istenen türü içermediğinden <xref:System.TypeLoadException> oluşur.

 Bu sorunu önlemek için, uygulamanızı oluşturan derlemelerin aynı derleme adına sahip olmadığından ve farklı dizinlerde aynı ada sahip derlemeler içerdiğinden emin olun.

> [!NOTE]
> .NET Framework, genel derleme önbelleğine tanımlayıcı adlandırılmış bir derleme yerleştirirseniz, derlemenin dosya adı, *. exe* veya *. dll*gibi dosya adı uzantısını dahil değil, derleme adıyla eşleşmelidir. Örneğin, bir derlemenin dosya adı *MyAssembly. dll*ise, derleme adının `myAssembly`olması gerekir. Yalnızca kök uygulama dizininde dağıtılan özel derlemeler, dosya adından farklı bir derleme adına sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir derlemenin tam nitelikli adını belirleme](find-fully-qualified-name.md)
- [Derlemeler oluştur](create.md)
- [Tanımlayıcı adlı derlemeler](strong-named.md)
- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
