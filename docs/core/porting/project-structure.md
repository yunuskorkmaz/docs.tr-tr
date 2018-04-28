---
title: Projeniz .NET Framework ve .NET Core desteklemek için düzenleme
description: .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri için yardımcı olur.
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5e2b56c325f54f49bf53b00c74a0e89137928c03
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Projeniz .NET Framework ve .NET Core desteklemek için düzenleme

Bu makalede, .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri yardımcı olur. Bu hedefe ulaşmak geliştiricilere yardımcı olmak için projeleri düzenlemek için çeşitli seçenekler sağlar. Aşağıdaki listede, ne zaman, proje düzeni .NET Core ile Kurulum nasıl karar dikkate alınması gereken bazı tipik senaryolar verilmiştir. Listenin istediğiniz her şeyi kapsayan değil; projenizin ihtiyaçlara göre öncelik verin.

* [**Var olan projeleri ve .NET Core projeler tek projelere birleştirin**][option-csproj]

  *Bu için iyi nedir:*
  * Yapı işleminizin tek bir proje derleme yerine her farklı bir .NET Framework sürümünü veya platformu hedefleme birden çok proje derleme basitleştirir.
  * Bir tek proje dosyası yönetmeniz gerekir çünkü çoklu hedefleyen projeler için kaynak dosyası yönetimini basitleştirir. Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projelerinizi bunlarla el ile eşitleme gerektirir.
  * Kolayca tüketimi için NuGet paketi oluşturuluyor.
  * Derleyici yönergeleri kullanarak, kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmayı sağlar.

  *Desteklenmeyen senaryolar:*
  * Geliştiriciler mevcut projeleri açmak için Visual Studio 2017 kullanmayı gerektirir. Visual Studio'nun daha eski sürümleri desteklemek için [proje dosyalarınızı farklı klasörlerde tutma](#support-vs) daha iyi bir seçenektir.

* <a name="support-vs"></a>[**Var olan projeleri ve yeni .NET Core projeler ayrı tut**][option-csproj-folder]

  *Bu için iyi nedir:*
  * Geliştiriciler/Visual Studio 2017 sahip olmaması katkıda bulunanlar için yükseltme yapmak zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam.
  * Kod karmaşası bu projelerde gerektirdiğinden yeni hatalar mevcut projelerinde oluşturma olasılığını azaltmak.

## <a name="example"></a>Örnek

Depo göz önünde bulundurun:

![Mevcut proje][example-initial-project]

[**Kaynak kodu**][example-initial-project-code]

Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Mevcut projeleri çoklu hedeflenen .NET Core projesi ile değiştir

Herhangi bir varolan deposu reorganıze  *\*.csproj* dosyaları kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur. Tek bir proje için farklı çerçeveleri derleme mümkün olduğundan bu harika bir seçenektir. Ayrıca, farklı derleme seçenekleri ve bağımlılıkları hedef çerçeveyi başına işlemek için güç sahiptir.

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma][example-csproj]

[**Kaynak kodu**][example-csproj-code]

Not değişiklik şunlardır:
* Değiştirilmesini *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj* ] [ example-csproj-netcore]. NuGet paketleri ile belirtilir `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Mevcut projeleri tutmak ve .NET Core projesi oluşturma

Eski çerçeveleri hedef mevcut projeleri varsa, bu projeler dokunulmadan bırakın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core proje kullanın isteyebilirsiniz.

![.NET core projeyle farklı klasörde mevcut proje][example-csproj-different-folder]

[**Kaynak kodu**][example-csproj-different-code]

Not değişiklik şunlardır:
* .NET Core ve mevcut projeleri ayrı klasörlerde tutulur.
    * Projeleri ayrı klasörlerde tutma Visual Studio 2017 olmasını zorlama önler. Yalnızca eski projeleri açar ayrı bir çözüm oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

Lütfen bakın [.NET Core belgeleri taşıma] [ porting-doc] .NET Core geçirme hakkında daha fazla yönlendirme için.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Mevcut proje"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Birden çok çerçeveyi hedefleyen bir csproj oluşturma"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Farklı bir klasör içinde varolan PCL .NET core projeyle"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
