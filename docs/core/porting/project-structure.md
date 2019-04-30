---
title: .NET Framework ve .NET Core için proje düzenleme
description: .NET Framework ve .NET Core yan yana karşı çözüm derlemek istediğiniz proje sahipleri için yardımcı olur.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: ab484ccc2c5b51b2ee1dca57df51669d288f3e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663211"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Hem .NET Framework ve .NET Core desteklemek için proje düzenleme

Hem .NET Framework ve .NET Core yan yana için derleyen bir çözüm oluşturmayı öğrenin. Bu amaca ulaşmak amacıyla projelerini düzenlemek için çeşitli seçenekler bakın. Ne zaman .NET Core projesi düzeninizi nasıl karar dikkate alınması gereken bazı tipik senaryolar aşağıda verilmiştir. Listeden istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verin.

* [**Var olan projeleri ve .NET Core projeleri tek projelere birleştirin**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Ne bu için uygundur:*
  * Yapı işleminizin, tek bir proje derlenirken yerine her platform veya farklı bir .NET Framework sürümünü hedefleyen birden çok proje derleme basitleştirir.
  * Tek bir proje dosyası yönetmeniz gerektiğinden çoklu hedefleyen projeler için kaynak dosya yönetimi basitleştirir. Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projeleriniz ile el ile eşitleme yapmanız gerekir.
  * Kolayca tüketim için bir NuGet paketi oluşturuluyor.
  * Derleyici yönergeleri kullanarak kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak sağlar.

  *Desteklenmeyen senaryolar:*
  * Var olan projeleri açmak için Visual Studio 2017 geliştiriciler gerektirir. Visual Studio'nun eski sürümlerini desteklemek üzere [farklı klasörlerde bulunan proje dosyalarınızı tutma](#support-vs) daha iyi bir seçenektir.

* <a name="support-vs"></a>[**Var olan projeleri ve yeni .NET Core projeleri ayrı tut**](#keep-existing-projects-and-create-a-net-core-project)

  *Ne bu için uygundur:*
  * Geliştiriciler/Visual Studio 2017 sahip olmayan katkıda bulunanlar için yükseltmek zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam ediliyor.
  * Bu projelerde hiçbir kod karmaşası olması gerektiğinden yeni hatalar var olan projeleri oluşturma olasılığını kısaltır.

## <a name="example"></a>Örnek

Aşağıdaki depoya göz önünde bulundurun:

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Var olan projeleri birden çok hedefli bir .NET Core projesi ile değiştirin.

Herhangi bir mevcut depoyu reorganıze  *\*.csproj* dosyalar kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur. Tek bir proje için farklı çerçeveler derleyemezsiniz olduğu için bu harika bir seçenektir. Ayrıca, farklı bir derleme seçenekleri ve bağımlılıkları hedeflenen çerçeve başına işleme gücüne sahiptir.

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Dikkat edilecek değişiklikler şunlardır:

* Değiştirme *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). NuGet paketleri ile belirtilen `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Var olan projeleri korumak ve bir .NET Core projesi oluşturma

Eski çerçeveleri hedefleyen var olan projeler varsa, bu projelerin dokunmayın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesinden kullanmak isteyebilirsiniz.

![Varolan projede, farklı bir klasör ile .NET core projesi](./media/project-structure/separate-projects-same-source.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Dikkat edilecek değişiklikler şunlardır:

* .NET Core ve mevcut projeleri ayrı klasörlerde tutulur.
  * Projeleri ayrı klasörlerde tutmak için Visual Studio 2017 için zorlama önler. Yalnızca eski projelerdeki açılır ayrı bir çözüm oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

Lütfen [.NET Core belgeleri taşıma](index.md) .NET Core ile geçirme hakkında daha fazla yardım almak için.
