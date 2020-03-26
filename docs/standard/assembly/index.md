---
title: .NET’te bütünleştirilmiş kodlar
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: b61d079a86bdd4a809d44ad128f19a7b358c8384
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228671"
---
# <a name="assemblies-in-net"></a>.NET’te bütünleştirilmiş kodlar

Derlemeler dağıtım, sürüm denetimi, yeniden kullanımı, etkinleştirme kapsam ve güvenlik izinleri için temel birimleri oluşturur. NET tabanlı uygulamalar. Bir derleme, birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan bir tür ve kaynakların bir derlemesidir. Derlemeler yürütülebilir (*.exe*) veya dinamik bağlantı kitaplığı (*.dll*) dosyaları biçimindedir ve .NET uygulamalarının yapı taşlarıdır. Ortak dil çalışma zamanını, tür uygulamalarına dikkat etmesi gereken bilgilerle birlikte sağlarlar.

.NET Core ve .NET Framework'de, bir veya daha fazla kaynak kod dosyasından derleme oluşturabilirsiniz. .NET Framework'de derlemeler bir veya daha fazla modül içerebilir. Bu, birden çok geliştiricinin tek bir derleme oluşturmak için birleştirilen ayrı kaynak kodu dosyaları veya modülleri üzerinde çalışabilmesi için daha büyük projelerin planlanmasını sağlar. Modüller hakkında daha fazla bilgi için [bkz.](../../framework/app-domains/build-multifile-assembly.md)

Derlemeler aşağıdaki özelliklere sahiptir:

- Derlemeler *.exe* veya *.dll* dosyaları olarak uygulanır.

- .NET Framework'ü hedefleyen kitaplıklar için, derlemeleri [genel derleme önbelleğine (GAC)](../../framework/app-domains/gac.md)koyarak uygulamalar arasında paylaşabilirsiniz. Bunları GAC'ye eklemeden önce derlemeleri güçlü adlandırmanız gerekir. Daha fazla bilgi için Bkz. [Güçlü adlı derlemeler.](strong-named.md)

- Derlemeler yalnızca gerekli yse belleğe yüklenir. Kullanılmazlarsa, yüklenmezler. Bu, derlemelerin daha büyük projelerdeki kaynakları yönetmenin etkili bir yolu olabileceği anlamına gelir.

- Yansımayı kullanarak bir derleme hakkında programlı olarak bilgi edinebilirsiniz. Daha fazla bilgi için [Yansıma (C#)](../../csharp/programming-guide/concepts/reflection.md) veya [Yansıma (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md)'ye bakın.

- Bir derlemeyi sadece .NET Core'daki <xref:System.Reflection.MetadataLoadContext> sınıfı ve .NET Core ve .NET Framework'deki <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> yöntemleri <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> kullanarak incelemek için yükleyebilirsiniz.

## <a name="assemblies-in-the-common-language-runtime"></a>Ortak dilde çalışma zamanındaki derlemeler

Derlemeler, tür uygulamalarına dikkat etmesi gereken bilgilerle ortak dil çalışma zamanını sağlar. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.

Derleme aşağıdaki bilgileri tanımlar:

- Ortak dil çalışma zamanının yürütüldettiği kod. Her derlemenin yalnızca bir giriş `DllMain`noktası `WinMain`olabileceğini `Main`unutmayın: , , veya .

- Güvenlik sınırı. Bir derleme, izinlerin istendiği ve verildiği birimdir. Derlemelerde güvenlik sınırları hakkında daha fazla bilgi için [Montaj güvenlik hususlarına](security-considerations.md)bakın.

- Sınır yazın. Her tipin kimliği, içinde bulunduğu derlemenin adını içerir. Bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan bir tür, başka bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan türle aynı değildir.

- Başvuru kapsamı sınırı. [Derleme bildirimi,](#assembly-manifest) türleri çözmek ve kaynak isteklerini karşılamak için kullanılan meta verilere sahiptir. Bildirim, derleme dışında ortaya çıkarmak için türleri ve kaynakları belirtir ve bağlı olduğu diğer derlemeleri toplar. Taşınabilir yürütülebilir (PE) dosyasındaki Microsoft ara dili (MSIL) kodu, ilişkili bir [derleme bildirimi](#assembly-manifest)olmadığı sürece yürütülmez.

- Sürüm sınırı. Derleme, ortak dil çalışma süresindeki en küçük sürülebilir birimdir. Aynı derlemedeki tüm türler ve kaynaklar bir birim olarak sürülür. [Derleme bildirimi,](#assembly-manifest) bağımlı derlemeler için belirttiğiniz sürüm bağımlılıklarını açıklar. Sürüm hakkında daha fazla bilgi için [Montaj sürümüne](versioning.md)bakın.

- Dağıtım birimi. Bir uygulama başlatıldığında, sadece uygulamanın başlangıçta çağırdığı derlemeler mevcut olmalıdır. Yerelleştirme kaynakları veya yardımcı program sınıfları içeren derlemeler gibi diğer derlemeler, isteğe bağlı olarak alınabilir. Bu, uygulamaların ilk indirildiğinde basit ve ince olmasını sağlar. Derlemeleri dağıtma hakkında daha fazla bilgi için [bkz.](../../framework/deployment/index.md)

- Yan yana yürütme birimi. Bir derlemenin birden çok sürümü çalıştırma hakkında daha fazla bilgi için [Derlemeler ve yan yana yürütme](side-by-side-execution.md)bölümüne bakın.

## <a name="create-an-assembly"></a>Derleme oluşturma

Derlemeler statik veya dinamik olabilir. Statik derlemeler, disk üzerinde taşınabilir yürütülebilir (PE) dosyalarda saklanır. Statik derlemeler arabirimleri, sınıfları ve bit eşlemler, JPEG dosyaları ve diğer kaynak dosyaları gibi kaynakları içerebilir. Ayrıca, doğrudan bellekten çalıştırılan ve yürütmeden önce diske kaydedilmemiş dinamik derlemeler de oluşturabilirsiniz. Yürütüldükten sonra dinamik derlemeleri diske kaydedebilirsiniz.

Derleme oluşturmak için birçok yol vardır. *.dll* veya *.exe* dosyaları oluşturabilen Visual Studio gibi geliştirme araçlarını kullanabilirsiniz. Diğer geliştirme ortamlarından modüllerle derlemeler oluşturmak için Windows SDK'daki araçları kullanabilirsiniz. Dinamik derlemeler oluşturmak için ortak dil <xref:System.Reflection.Emit?displayProperty=nameWithType>çalışma zamanı API'lerini de kullanabilirsiniz.

Derleme derlemeleri Visual Studio'da oluşturarak, .NET Core komut satırı arabirim araçlarıyla oluşturarak veya .NET Framework derlemesini komut satırı derleyicisiyle oluşturarak derlemeyapın. .NET Core CLI kullanarak derlemeler oluşturma hakkında daha fazla bilgi için [bkz.](../../core/tools/index.md) Komut satırı derleyicileri ile derlemeler oluşturmak için C#için [csc.exe ile komut satırı oluşturma](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya Visual Basic için komut [satırından Yapı'ya](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) bakın.

> [!NOTE]
> Visual Studio'da derleme oluşturmak için **Yapı** menüsünde **Oluştur'u**seçin.

## <a name="assembly-manifest"></a>Derleme bildirimi

Her derlemenin bir *derleme bildirim* dosyası vardır. İçindekiler tablosuna benzer şekilde, derleme bildirimi şunları içerir:

- Derlemenin kimliği (adı ve sürümü).

- *.exe* veya *.dll* dosyanızın dayandığı diğer derlemeler, bitmap dosyaları veya Readme dosyaları gibi derlemeyi oluşturan diğer tüm dosyaları açıklayan bir dosya tablosu.

- *.dll*s veya diğer dosyalar gibi tüm dış akçelerin listesi olan *derleme başvuru listesi.* Derleme başvuruları hem genel hem de özel nesnelere başvurular içerir. Genel nesneler diğer tüm uygulamalar için kullanılabilir. .NET Core'da, genel nesneler belirli bir .NET Core çalışma süresiyle birleştiğinde. .NET Framework'de, genel nesneler genel montaj önbelleğinde (GAC) bulunur. *System.IO.dll* GAC bir derleme bir örnektir. Özel nesneler, uygulamanızın yüklendiği dizinde veya altında dizin düzeyinde olmalıdır.

Derlemeler içerik, sürüm ve bağımlılıklar hakkında bilgi içerdiğinden, bunları kullanan uygulamaların düzgün çalışması için Windows sistemlerindeki kayıt defteri gibi dış kaynaklara dayanması gerekmez. Derlemeler *.dll* çakışmalarını azaltır ve uygulamalarınızın daha güvenilir ve dağıtılmasını kolaylaştırır. Birçok durumda, bir . NET tabanlı uygulama sadece hedef bilgisayara dosyalarını kopyalayarak. Daha fazla bilgi için [Derleme bildirimine](manifest.md)bakın.

## <a name="add-a-reference-to-an-assembly"></a>Derlemeye başvuru ekleme

Bir uygulamada derleme kullanmak için, buna bir başvuru eklemeniz gerekir. Bir derleme başvurulduktan sonra, ad alanlarının tüm erişilebilir türleri, özellikleri, yöntemleri ve diğer üyeleri, kodları kaynak dosyanızın bir parçasıyılmış gibi uygulamanız tarafından kullanılabilir.

> [!NOTE]
> .NET Sınıf Kitaplığı'ndaki derlemelerin çoğuna otomatik olarak başvurulur. Bir sistem derlemesi otomatik olarak başvurulmuyorsa, .NET Core için, derlemeyi içeren NuGet paketine bir başvuru ekleyebilirsiniz. Visual Studio'da NuGet Paket Yöneticisi'ni kullanın veya *.csproj* veya *.vbproj* projesine montaj için [ \<packagereference>](../../core/tools/dependencies.md#the-packagereference-element) öğesi ekleyin. .NET Framework'de, Visual Studio'daki Başvuru **Ekle** iletişim kutusunu kullanarak veya [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) veya [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) derleyicileri için `-reference` komut satırı seçeneğini kullanarak derlemeye bir başvuru ekleyebilirsiniz.

C#'da, aynı derlemenin iki sürümütek bir uygulamada kullanabilirsiniz. Daha fazla bilgi için [extern diğer adı.](../../csharp/language-reference/keywords/extern-alias.md)

## <a name="related-content"></a>İlgili içerik

|Başlık|Açıklama|
|-----------|-----------------|
|[Montaj içeriği](contents.md)|Bir derlemeoluşturan öğeler.|
|[Montaj manifestosu](manifest.md)|Derlemedeki veriler ve derlemelerde nasıl depolanır.|
|[Genel montaj önbelleği](../../framework/app-domains/gac.md)|GAC derlemeleri nasıl saklar ve kullanır.|
|[Güçlü adlandırılmış derlemeler](strong-named.md)|Güçlü adlandırılmış derlemelerin özellikleri.|
|[Derleme güvenliği hakkında dikkate alınması gerekenler](security-considerations.md)|Güvenlik meclislerde nasıl çalışır.|
|[Montaj sürümü](versioning.md)|.NET Framework sürüm ilkesine genel bakış.|
|[Montaj yerleşimi](../../framework/app-domains/assembly-placement.md)|Montajların bulunduğu yer.|
|[Derlemeler ve yan yana yürütme](side-by-side-execution.md)|Aynı anda çalışma zamanının veya derlemenin birden çok sürümü kullanın.|
|[Dinamik metotları ve bütünleştirilmiş kodları yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler nasıl oluşturulur.|
|[Çalışma zamanı derlemeleri nasıl bulur?](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|.NET Framework'ün montaj başvurularını çalışma zamanında nasıl çözer?|

## <a name="reference"></a>Başvuru

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleme dosya biçimi](file-format.md)
- [Arkadaş meclisleri](friend.md)
- [Başvuru derlemeleri](reference-assemblies.md)
- [Nasıl yapılsın: Montajları yükleme ve boşaltma](load-unload.md)
- [Nasıl kullanılır: .NET Core'da montaj boşaltılabilirliğini kullanma ve hata ayıklama](unloadability.md)
- [Nasıl Yapılır: Dosyanın derleme olup olmadığını belirleme](identify.md)
- [Nasıl yapilir: MetadataLoadContext kullanarak montaj içeriğini inceleyin](inspect-contents-using-metadataloadcontext.md)
