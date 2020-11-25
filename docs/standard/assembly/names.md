---
title: Derleme adları
description: .NET derleme adları ve bunların derleme kapsamı üzerinde etkileri ve bir uygulama tarafından kullanımı hakkında bilgi edinin ve FullName özelliği hakkında bilgi edinin.
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET], assemblies
- assemblies [.NET], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 9aa94b4ee54c0a663c9f38392d37369af9f27e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731455"
---
# <a name="assembly-names"></a>Derleme adları

Bir derlemenin adı meta verilerde depolanır ve derlemenin kapsamı üzerinde önemli bir etkiye sahiptir ve bir uygulama tarafından kullanılır. Tanımlayıcı adlı bütünleştirilmiş kod, derleme adı, kültür, ortak anahtar, sürüm numarası ve isteğe bağlı olarak işlemci mimarisini içeren tam nitelikli bir ada sahiptir. <xref:System.Reflection.Assembly.FullName%2A>Yüklenen derlemeler için genellikle görünen ad olarak adlandırılan tam adı almak için özelliğini kullanın.

Çalışma zamanı, derlemeyi bulmak ve aynı ada sahip diğer derlemelerden ayırt etmek için ad bilgilerini kullanır. Örneğin, bilinen bir tanımlayıcı adlı derleme `myTypes` aşağıdaki tam ada sahip olabilir:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

Bu örnekte, tam nitelikli ad, `myTypes` derlemenin ortak anahtar belirtecine sahip bir tanımlayıcı ada sahip olduğunu, Birleşik Devletler İngilizce için kültür değerine sahip olduğunu ve 1.0.1234.0 sürüm numarasına sahip olduğunu gösterir. İşlemci mimarisi, `msil` tam zamanında (JIT) olarak derlenen ve işletim sistemine ve işlemciye bağlı olarak 32 bitlik koda veya 64 bit koda derlenmiş olacaktır.

> [!TIP]
> `ProcessorArchitecture`Bilgiler, derlemelerin işlemciye özgü sürümlerine izin verir. Kimliği yalnızca işlemci mimarisine göre farklılık gösteren bir derlemenin sürümlerini oluşturabilirsiniz, örneğin, 32 bit ve 64 bit işlemciye özgü sürümler. Güçlü adlar için işlemci mimarisi gerekli değildir. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Bir derlemede tür isteyen kodun tam bir derleme adı kullanması gerekir. Bu, tam olarak nitelenmiş bağlama olarak adlandırılır. Yalnızca bir derleme adı belirten kısmi bağlamaya .NET Framework içindeki derlemelere başvurulması sırasında izin verilmez.

 .NET Framework oluşturan derlemelere yapılan tüm derleme başvuruları, derlemenin tam nitelikli adını da içermelidir. Örneğin, 1,0 sürümü için System. Data .NET Framework derlemesine bir başvuru şunları içerir:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

Sürüm, .NET Framework sürüm 1,0 ile birlikte gelen tüm .NET Framework derlemelerinin sürüm numarasına karşılık gelir. .NET Framework derlemeleri için kültür değeri her zaman tarafsız olur ve ortak anahtar Yukarıdaki örnekte gösterilen şekilde aynıdır.

 Örneğin, bir izleme dinleyicisi ayarlamak için bir yapılandırma dosyasına bir derleme başvurusu eklemek için, sistem .NET Framework derlemesinin tam nitelikli adını dahil edersiniz:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Çalışma zamanı derleme adlarını bir derlemeye bağlarken büyük/küçük harfe duyarsız olarak değerlendirir, ancak bir derleme adında hangi durumun kullanıldığını korur. Windows SDK çeşitli araçlar, derleme adlarını büyük/küçük harfe duyarlı olarak işler. En iyi sonuçlar için, derleme adlarını büyük küçük harfe duyarlı olsalar gibi yönetin.

## <a name="name-application-components"></a>Uygulama bileşenlerini Adlandır

 Çalışma zamanı, bir derlemenin kimliğini belirlerken dosya adını dikkate almaz. Derleme adı, sürüm, kültür ve tanımlayıcı adından oluşan derleme kimliğinin çalışma zamanına açık olması gerekir.

 Örneğin, *myAssembly.dll* adlı bir derlemeye başvuran *myAssembly.exe* adlı bir derlemeye sahipseniz, *myAssembly.exe* çalıştırırsanız bağlama doğru bir şekilde gerçekleşir. Ancak, yöntemi kullanarak başka bir uygulama *myAssembly.exe* yürütülüyorsa <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> , çalışma zamanı, `myAssembly` *myAssembly.exe* istekleri istediğinde zaten yüklü olduğunu belirler `myAssembly` . Bu durumda *myAssembly.dll* hiçbir şekilde yüklenmez. *myAssembly.exe* istenen türü içermediğinden, bir <xref:System.TypeLoadException> meydana gelir.

 Bu sorunu önlemek için, uygulamanızı oluşturan derlemelerin aynı derleme adına sahip olmadığından ve farklı dizinlerde aynı ada sahip derlemeler içerdiğinden emin olun.

> [!NOTE]
> .NET Framework, genel derleme önbelleğine tanımlayıcı adlandırılmış bir derleme yerleştirirseniz, derlemenin dosya adı, *. exe* veya *. dll* gibi dosya adı uzantısını dahil değil, derleme adıyla eşleşmelidir. Örneğin, bir derlemenin dosya adı *myAssembly.dll*, derleme adı olmalıdır `myAssembly` . Yalnızca kök uygulama dizininde dağıtılan özel derlemeler, dosya adından farklı bir derleme adına sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir derlemenin tam nitelikli adını belirleme](find-fully-qualified-name.md)
- [Derleme oluşturma](create.md)
- [Tanımlayıcı adlandırılmış derlemeler](strong-named.md)
- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
