---
title: .NET Framework ve .NET Core için proje düzenleme
description: .NET Framework ve .NET Core yan yana karşı çözüm derlemek istediğiniz proje sahipleri için yardımcı olur.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 4f3469c7f5c8c95cb5bf2ce522c8732c90744755
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759671"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Hem .NET Framework ve .NET Core desteklemek için proje düzenleme

Hem .NET Framework ve .NET Core yan yana için derleyen bir çözüm oluşturmayı öğrenin. Bu amaca ulaşmak amacıyla projelerini düzenlemek için çeşitli seçenekler bakın. Ne zaman .NET Core projesi düzeninizi nasıl karar dikkate alınması gereken bazı tipik senaryolar aşağıda verilmiştir. Listeden istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verin.

* [**Var olan projeleri ve .NET Core projeleri tek projelere birleştirin**][option-csproj]

  *Ne bu için uygundur:*
  * Yapı işleminizin, tek bir proje derlenirken yerine her platform veya farklı bir .NET Framework sürümünü hedefleyen birden çok proje derleme basitleştirir.
  * Tek bir proje dosyası yönetmeniz gerektiğinden çoklu hedefleyen projeler için kaynak dosya yönetimi basitleştirir. Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projeleriniz ile el ile eşitleme yapmanız gerekir.
  * Kolayca tüketim için bir NuGet paketi oluşturuluyor.
  * Derleyici yönergeleri kullanarak kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak sağlar.

  *Desteklenmeyen senaryolar:*
  * Var olan projeleri açmak için Visual Studio 2017 geliştiriciler gerektirir. Visual Studio'nun eski sürümlerini desteklemek üzere [farklı klasörlerde bulunan proje dosyalarınızı tutma](#support-vs) daha iyi bir seçenektir.

* <a name="support-vs"></a>[**Var olan projeleri ve yeni .NET Core projeleri ayrı tut**][option-csproj-folder]

  *Ne bu için uygundur:*
  * Geliştiriciler/Visual Studio 2017 sahip olmayan katkıda bulunanlar için yükseltmek zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam ediliyor.
  * Bu projelerde hiçbir kod karmaşası olması gerektiğinden yeni hatalar var olan projeleri oluşturma olasılığını kısaltır.

## <a name="example"></a>Örnek

Aşağıdaki depoya göz önünde bulundurun:

![Mevcut proje][example-initial-project]

[**Kaynak kodu**][example-initial-project-code]

Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Var olan projeleri birden çok hedefli bir .NET Core projesi ile değiştirin.

Herhangi bir mevcut depoyu reorganıze  *\*.csproj* dosyalar kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur. Tek bir proje için farklı çerçeveler derleyemezsiniz olduğu için bu harika bir seçenektir. Ayrıca, farklı bir derleme seçenekleri ve bağımlılıkları hedeflenen çerçeve başına işleme gücüne sahiptir.

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma][example-csproj]

[**Kaynak kodu**][example-csproj-code]

Dikkat edilecek değişiklikler şunlardır:

* Değiştirme *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj* ] [ example-csproj-netcore]. NuGet paketleri ile belirtilen `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Var olan projeleri korumak ve bir .NET Core projesi oluşturma

Eski çerçeveleri hedefleyen var olan projeler varsa, bu projelerin dokunmayın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesinden kullanmak isteyebilirsiniz.

![Varolan projede, farklı bir klasör ile .NET core projesi][example-csproj-different-folder]

[**Kaynak kodu**][example-csproj-different-code]

Dikkat edilecek değişiklikler şunlardır:

* .NET Core ve mevcut projeleri ayrı klasörlerde tutulur.
  * Projeleri ayrı klasörlerde tutmak için Visual Studio 2017 için zorlama önler. Yalnızca eski projelerdeki açılır ayrı bir çözüm oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

Lütfen [.NET Core belgeleri taşıma] [ porting-doc] .NET Core ile geçirme hakkında daha fazla yardım almak için.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Mevcut proje"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Birden çok çerçeveyi hedefleyen bir csproj oluşturma"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Var olan farklı bir klasöre PCL'de ile .NET core projesi"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
