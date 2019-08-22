---
title: .NET’te bütünleştirilmiş kodlar
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 09dc44141a4eea7601df3f918e8740efdb99aeda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666598"
---
# <a name="assemblies-in-net"></a>.NET’te bütünleştirilmiş kodlar

Derlemeler bir için temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleri oluşturur. NET tabanlı uygulama. Derlemeler bir yürütülebilir (. exe) dosya veya dinamik bağlantı kitaplığı (. dll) dosyası biçimini alır ve .NET uygulamalarının yapı taşlarıdır. Ortak dil çalışma zamanını, tür uygulamalarının farkında olması için gereken bilgileri sağlar. Bir derlemeyi, mantıksal bir işlev oluşturan ve birlikte çalışmak üzere tasarlanan tür ve kaynak koleksiyonu olarak düşünebilirsiniz.

.NET Core ve .NET Framework, bir derleme bir veya daha fazla kaynak kodu dosyasından oluşturulabilir. .NET Framework, derlemeler bir veya daha fazla modül içerebilir. Bu, çok sayıda projenin, tek bir derleme oluşturmak için birleştirilen ayrı kaynak kodu dosyaları veya modüller üzerinde çalışması için bu şekilde daha büyük projelerin planlanmasını sağlar. Modüller hakkında daha fazla bilgi için bkz [. nasıl yapılır: Çok dosyalı bütünleştirilmiş kod](../../framework/app-domains/how-to-build-a-multifile-assembly.md)oluşturun.

Derlemeler aşağıdaki özelliklere sahiptir:

- Derlemeler. exe veya. dll dosyaları olarak uygulanır.

- .NET Framework hedefleyen kitaplıklar için, bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](../../framework/app-domains/gac.md)yerleştirerek uygulamalar arasında paylaşabilirsiniz. Derlemeler, genel derleme önbelleğine eklenmek için tanımlayıcı adlandırılmış olmalıdır. Daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](../../framework/app-domains/strong-named-assemblies.md).

- Derlemeler yalnızca gerekli olmaları durumunda belleğe yüklenir. Bunlar kullanılmıyorsa, yüklenmez. Bu, derlemelerin daha büyük projelerde kaynakları yönetmenin etkili bir yolu olabileceği anlamına gelir.

- Yansıma kullanarak, bir derleme hakkında program aracılığıyla bilgi edinebilirsiniz. Daha fazla bilgi için bkz. [ReflectionC#()](../../csharp/programming-guide/concepts/reflection.md) veya [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Bir derlemeyi yalnızca <xref:System.Reflection.MetadataLoadContext> sınıfını kullanarak incelemek üzere yükleyebilirsiniz.

## <a name="assembly-manifest"></a>Derleme bildirimi

Her derleme içinde bir *derleme bildirimidir*. İçindekiler tablosuna benzer şekilde, derleme bildirimi şunları içerir:

- Derlemenin kimliği (adı ve sürümü).

- . Exe veya. dll dosyanızın dayandığı veya hatta bit eşlem ya da Benioku dosyaları için oluşturduğunuz diğer derlemeler gibi, derlemeyi oluşturan diğer tüm dosyaları tanımlayan bir dosya tablosu.

- Tüm dış bağımlılıkların listesi olan bir *derleme başvuru listesi*(. dll 'ler veya uygulamanızın ihtiyaç duyacağı başka dosyalar). Derleme başvuruları hem genel hem de özel nesneler için başvurular içerir. Genel nesneler diğer tüm uygulamalar tarafından kullanılabilir. .NET Core 'da, belirli bir .NET Core çalışma zamanı ile birlikte bulunur. .NET Framework, genel derleme önbelleğinde bulunurlar. <xref:System.IO?displayProperty=nameWithType> Ad alanı, genel derleme önbelleğindeki bir derlemeye bir örnektir. Özel nesneler, uygulamanızın yüklendiği dizin ile aynı düzeyde veya altında bir dizinde olmalıdır.

Derlemeler içerik, sürüm oluşturma ve Bağımlılıklar hakkında bilgi içerdiğinden, bunları kullanan uygulamaların düzgün çalışması için Windows kayıt defteri değerlerini kullanması gerekmez. Derlemeler. dll çakışmalarını azaltır ve uygulamalarınızın dağıtımını daha güvenilir ve daha kolay hale getirir. Çoğu durumda, bir yükleyebilirsiniz. Yalnızca dosyalarını hedef bilgisayara kopyalayarak NET tabanlı uygulama. Daha fazla bilgi için bkz. [derleme bildirimi](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Bir derlemeye başvuru ekleme

Bir derlemeyi kullanmak için buna bir başvuru eklemeniz gerekir. Ardından, kullanmak istediğiniz öğelerin ad alanını seçmek için C# Visual Basic için [using yönergesini](../../csharp/language-reference/keywords/using-directive.md) veya [Imports ifadesini](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kullanabilirsiniz. Bir derlemeye başvurulduktan ve içeri aktarıldıktan sonra, tüm erişilebilir türler, özellikler, Yöntemler ve ad alanlarının diğer üyeleri, kodu kaynak dosyanızın bir parçası olduğundan, uygulamanız için kullanılabilir.

> [!NOTE]
> .NET sınıf kitaplığındaki çoğu derlemeye otomatik olarak başvurulur. Ancak bazı durumlarda, bir sistem derlemesine otomatik olarak başvurulmayabilir. .NET Core 'da, Visual Studio 'da NuGet Paket Yöneticisi 'ni kullanarak veya derleme için *. csproj veya *. vbproj projesine bir [ \<packagereference >](../../core/tools/dependencies.md#the-new-packagereference-element) öğesi ekleyerek, derlemeyi içeren NuGet paketine bir başvuru ekleyebilirsiniz. .NET Framework, Visual Studio 'daki **Başvuru Ekle** iletişim kutusunu veya `-reference` [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) derleyicileri için [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) komut satırı seçeneğini kullanarak derlemeye başvuru ekleyebilirsiniz.

' C#De, tek bir uygulamada aynı derlemenin iki sürümünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [extern diğer ad](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Derleme oluşturma

Uygulamanızı, .NET Core komut satırı arabirimi (CLı) araçlarını kullanarak veya komut satırı derleyicisi ile .NET Framework derlemeleri oluşturarak, Visual Studio 'da oluşturarak uygulamanızı derleyin. .NET CLı araçları kullanarak derlemeler oluşturma hakkında daha fazla bilgi için bkz. [.NET Core komut satırı arabirimi (CLI) araçları](../../core/tools/index.md). Komut satırı derleyicileri olan derlemeler oluşturmak için, Visual Basic için komut satırından [CSC. exe ile birlikte komut satırı oluşturma](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) C# ve [oluşturma](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) bölümüne bakın.

> [!NOTE]
> Visual Studio 'da bir derleme oluşturmak için, **Yapı** menüsünde **Oluştur**' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleme dosyası biçimi](file-format.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Arkadaş Bütünleştirilmiş Kodları](friend-assemblies.md)
- [Nasıl yapılır: Derlemeleri (C#) yükle ve Kaldır](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Nasıl yapılır: Derlemeleri yükle ve Kaldır (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Nasıl yapılır: .NET Core’da Bütünleştirilmiş Kodu Kaldırabilme Özelliğini Kullanma ve Sorun Giderme](unloadability-howto.md)
- [Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
