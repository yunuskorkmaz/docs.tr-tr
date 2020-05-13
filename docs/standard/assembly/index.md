---
title: .NET’te bütünleştirilmiş kodlar
description: Derlemeler, için temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleridir. NET tabanlı uygulamalar.
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
ms.openlocfilehash: 87030bf9770c464709559b2fb8f4c0004009e48d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379908"
---
# <a name="assemblies-in-net"></a>.NET’te bütünleştirilmiş kodlar

Derlemeler, için temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleri birimlerini oluşturur. NET tabanlı uygulamalar. Bir derleme, birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan bir tür ve kaynakların bir derlemesidir. Derlemeler yürütülebilir (*. exe*) veya dinamik bağlantı kitaplığı (*. dll*) dosyaları formunu alır ve .NET uygulamalarının yapı taşlarıdır. Ortak dil çalışma zamanını, tür uygulamalarının farkında olması için gereken bilgileri sağlar.

.NET Core ve .NET Framework ' de bir veya daha fazla kaynak kodu dosyasından derleme oluşturabilirsiniz. .NET Framework, derlemeler bir veya daha fazla modül içerebilir. Bu, birçok geliştiricinin tek bir derleme oluşturmak için birleştirilen ayrı kaynak kod dosyaları veya modüller üzerinde çalışabilmesi için daha büyük projelerin planlanmasını sağlar. Modüller hakkında daha fazla bilgi için bkz. [nasıl yapılır: çok dosyalı derleme oluşturma](../../framework/app-domains/build-multifile-assembly.md).

Derlemeler aşağıdaki özelliklere sahiptir:

- Derlemeler *. exe* veya *. dll* dosyaları olarak uygulanır.

- .NET Framework hedefleyen kitaplıklar için, derlemeleri [genel derleme önbelleği 'ne (GAC)](../../framework/app-domains/gac.md)koyarak uygulamalar arasında paylaşabilirsiniz. GAC 'ye dahil etmeden önce derlemeleri tanımlayıcı olarak adlandırın. Daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](strong-named.md).

- Derlemeler yalnızca gerekli olmaları durumunda belleğe yüklenir. Kullanılmıyorsa, bunlar yüklenmez. Bu, derlemelerin daha büyük projelerde kaynakları yönetmenin etkili bir yolu olabileceği anlamına gelir.

- Yansıma kullanarak, bir derleme hakkında program aracılığıyla bilgi edinebilirsiniz. Daha fazla bilgi için bkz. [yansıma (C#)](../../csharp/programming-guide/concepts/reflection.md) veya [yansıma (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- <xref:System.Reflection.MetadataLoadContext>.NET Core içindeki sınıfını ve <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> .net Core ve .NET Framework yöntemlerini kullanarak incelemek için bir derlemeyi yükleyebilirsiniz.

## <a name="assemblies-in-the-common-language-runtime"></a>Ortak dil çalışma zamanındaki derlemeler

Derlemeler, tür uygulamalarının farkında olması için gereken bilgilerle ortak dil çalışma zamanı sağlar. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.

Bir derleme aşağıdaki bilgileri tanımlar:

- Ortak dil çalışma zamanının yürütüldüğünü belirten kod. Her derlemenin yalnızca bir giriş noktası olabileceğini unutmayın: `DllMain` , `WinMain` , veya `Main` .

- Güvenlik sınırı. Bir derleme, izinlerin istendiği ve verildiği birimdir. Derlemelerdeki güvenlik sınırları hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](security-considerations.md).

- Tür sınırı. Her tipin kimliği, içinde bulunduğu derlemenin adını içerir. Bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan bir tür, başka bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan türle aynı değildir.

- Başvuru kapsamı sınırı. [Bütünleştirilmiş kod bildiriminde](#assembly-manifest) , türleri çözümlemek ve kaynak isteklerini karşılayan meta veriler vardır. Bildirim, derleme dışında kullanıma sunulacak türleri ve kaynakları belirtir ve üzerinde bağımlı olduğu diğer derlemeleri numaralandırır. Bir Taşınabilir çalıştırılabilir (PE) dosyada Microsoft ara dili (MSIL) kodu, ilişkili bir [derleme bildirimine](#assembly-manifest)sahip olmadığı takdirde yürütülmez.

- Sürüm sınırı. Derleme, ortak dil çalışma zamanındaki en düşük sürümlenebilir birimdir. Aynı derlemedeki tüm türler ve kaynaklar birim olarak sürümlüdür. [Derleme bildirimi](#assembly-manifest) , herhangi bir bağımlı derleme için belirttiğiniz sürüm bağımlılıklarını açıklar. Sürüm oluşturma hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](versioning.md).

- Dağıtım birimi. Bir uygulama başlatıldığında, sadece uygulamanın başlangıçta çağırdığı derlemeler mevcut olmalıdır. Yerelleştirme kaynaklarını veya yardımcı sınıfları içeren derlemeler gibi diğer derlemeler isteğe bağlı olarak alınabilir. Bu, uygulamaların ilk İndirilme sırasında basit ve ince olmasını sağlar. Derlemeleri dağıtma hakkında daha fazla bilgi için bkz. [uygulamaları dağıtma](../../framework/deployment/index.md).

- Yan yana yürütme birimi. Bir derlemenin birden çok sürümünü çalıştırma hakkında daha fazla bilgi için bkz. [derlemeler ve yan yana yürütme](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Derleme oluştur

Derlemeler statik veya dinamik olabilir. Statik derlemeler, disk üzerinde taşınabilir yürütülebilir (PE) dosyalarda saklanır. Statik derlemeler, arabirimler, sınıflar ve bit eşlemler, JPEG dosyaları ve diğer kaynak dosyaları gibi kaynakları içerebilir. Ayrıca, doğrudan bellekten çalıştırılan ve yürütmeden önce diske kaydedilmemiş dinamik derlemeler de oluşturabilirsiniz. Yürütüldükten sonra dinamik derlemeleri diske kaydedebilirsiniz.

Derleme oluşturmak için birçok yol vardır. Visual Studio gibi, *. dll* veya *. exe* dosyaları oluşturabileceğiniz geliştirme araçlarını kullanabilirsiniz. Diğer geliştirme ortamlarındaki modüllerle derlemeler oluşturmak için Windows SDK araçlarını kullanabilirsiniz. Dinamik derlemeler oluşturmak için gibi ortak dil çalışma zamanı API 'Lerini de kullanabilirsiniz <xref:System.Reflection.Emit?displayProperty=nameWithType> .

Derlemeleri Visual Studio 'da oluşturarak, .NET Core komut satırı arabirimi araçlarıyla derleyerek veya komut satırı derleyicisi ile .NET Framework derlemeleri oluştururken derleyin. .NET Core CLI kullanarak derlemeler oluşturma hakkında daha fazla bilgi için bkz. [.NET Core CLI genel bakış](../../core/tools/index.md). Komut satırı derleyicileri ile derleme oluşturmak için, bkz. C# için [CSC. exe Ile komut satırı derleme](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya Visual Basic için [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) .

> [!NOTE]
> Visual Studio 'da derleme oluşturmak için, **Oluştur** menüsünde, **Oluştur**' u seçin.

## <a name="assembly-manifest"></a>Derleme bildirimi

Her derlemenin bir *bütünleştirilmiş kod bildirim* dosyası vardır. İçindekiler tablosuna benzer şekilde, derleme bildirimi şunları içerir:

- Derlemenin kimliği (adı ve sürümü).

- *. Exe* veya *. dll* dosyanızın dayandığı, oluşturduğunuz diğer derlemeler, bit eşlem dosyaları veya Benioku dosyaları gibi, derlemeyi oluşturan diğer tüm dosyaları açıklayan bir dosya tablosu.

- *. Dll*s veya diğer dosyalar gibi tüm dış bağımlılıkların listesi olan bir *derleme başvuru listesi*. Derleme başvuruları hem genel hem de özel nesneler için başvurular içerir. Genel nesneler diğer tüm uygulamalar tarafından kullanılabilir. .NET Core 'da, genel nesneler belirli bir .NET Core çalışma zamanı ile birlikte işlenir. .NET Framework, genel nesneler genel derleme önbelleğinde (GAC) bulunur. *System. IO. dll* GAC 'deki bir derlemeye örnektir. Özel nesneler, uygulamanızın yüklendiği dizinin üzerinde veya altında bir dizin düzeyinde olmalıdır.

Derlemeler içerik, sürüm oluşturma ve Bağımlılıklar hakkında bilgi içerdiğinden, bunları kullanan uygulamalar Windows sistemlerindeki kayıt defteri gibi dış kaynakları değil, düzgün şekilde çalışır. Derlemeler *. dll* çakışmalarını azaltır ve uygulamalarınızın dağıtımını daha güvenilir ve daha kolay hale getirir. Çoğu durumda, bir yükleyebilirsiniz. Yalnızca dosyalarını hedef bilgisayara kopyalayarak NET tabanlı uygulama. Daha fazla bilgi için bkz. [derleme bildirimi](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Bir derlemeye başvuru ekleme

Bir uygulamada bir derlemeyi kullanmak için buna bir başvuru eklemeniz gerekir. Bir derlemeye başvurulduktan sonra, tüm erişilebilir türler, özellikler, Yöntemler ve ad alanlarının diğer üyeleri, kodu kaynak dosyanızın bir parçası olduğundan, uygulamanız için kullanılabilir.

> [!NOTE]
> .NET sınıf kitaplığındaki çoğu derlemeye otomatik olarak başvurulur. Bir sistem derlemesine otomatik olarak başvurulmazsa, .NET Core için derlemeyi içeren NuGet paketine bir başvuru ekleyebilirsiniz. Visual Studio 'da NuGet paket yöneticisini kullanın veya *. csproj* veya *. vbproj* projesine derleme için bir [ \< packagereference>](../../core/tools/dependencies.md#the-packagereference-element) öğesi ekleyin. .NET Framework, Visual Studio 'da **Başvuru Ekle** iletişim kutusunu kullanarak veya `-reference` [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) veya [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) derleyicileri için komut satırı seçeneğini kullanarak derlemeye bir başvuru ekleyebilirsiniz.

C# ' de, tek bir uygulamada aynı derlemenin iki sürümünü kullanabilirsiniz. Daha fazla bilgi için bkz. [extern diğer ad](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>İlgili içerik

|Başlık|Açıklama|
|-----------|-----------------|
|[Derleme içerikleri](contents.md)|Bir derlemeyi oluşturan öğeler.|
|[Derleme bildirimi](manifest.md)|Derleme bildirimindeki veriler ve derlemelerde nasıl depolanıyor.|
|[Genel derleme önbelleği](../../framework/app-domains/gac.md)|GAC derlemeleri nasıl depolar ve kullanır.|
|[Tanımlayıcı adlandırılmış derlemeler](strong-named.md)|Tanımlayıcı adlı derlemelerin özellikleri.|
|[Derleme güvenliği hakkında dikkate alınması gerekenler](security-considerations.md)|Güvenlik, Derlemelerle nasıl kullanılır.|
|[Derleme sürümü oluşturma](versioning.md)|.NET Framework sürüm oluşturma ilkesine genel bakış.|
|[Derleme yerleştirme](../../framework/app-domains/assembly-placement.md)|Derlemelerin nerede bulunacağı.|
|[Derlemeler ve yan yana yürütme](side-by-side-execution.md)|Çalışma zamanının veya derlemenin birden çok sürümünü aynı anda kullanın.|
|[Dinamik metotları ve bütünleştirilmiş kodları yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler oluşturma.|
|[Çalışma zamanının derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|.NET Framework çalışma zamanında derleme başvurularını nasıl çözümler.|

## <a name="reference"></a>Başvuru

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleme dosyası biçimi](file-format.md)
- [Arkadaş derlemeleri](friend.md)
- [Başvuru derlemeleri](reference-assemblies.md)
- [Nasıl yapılır: derlemeleri yükleme ve kaldırma](load-unload.md)
- [Nasıl yapılır: .NET Core 'da derleme tasbilirliğini kullanma ve hata ayıklama](unloadability.md)
- [Nasıl yapılır: bir dosyanın derleme olup olmadığını belirleme](identify.md)
- [Nasıl yapılır: MetadataLoadContext kullanarak bütünleştirilmiş kod içeriklerini Inceleme](inspect-contents-using-metadataloadcontext.md)
