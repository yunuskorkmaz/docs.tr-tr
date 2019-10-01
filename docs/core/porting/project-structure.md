---
title: .NET Framework ve .NET Core için projeleri düzenleme
description: Çözümlerini .NET Framework ve .NET Core ile yan yana derlemek isteyen proje sahipleri için yardım.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 1e120e1aee60e88ea33a8290f3bf36eb93bfc91c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698930"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Projenizi hem .NET Framework hem de .NET Core 'ı destekleyecek şekilde düzenleyin

Hem .NET Framework hem de .NET Core yan yana için derlenen bir çözüm oluşturmayı öğrenin. Bu amaca ulaşmanıza yardımcı olmak için projeleri düzenlemek için çeşitli seçeneklere bakın. İşte, proje düzeninizi .NET Core ile ayarlama konusunda karar verirken göz önünde bulundurmanız gereken bazı tipik senaryolar aşağıda verilmiştir. Liste istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verir.

* [**Mevcut projeleri ve .NET Core projelerini tek projeler halinde birleştirin**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Bunun için uygun olan şey:*
  * Her biri farklı bir .NET Framework sürümü veya platformu hedefleyen birden çok proje derlemek yerine, tek bir projeyi derleyerek yapı işleminizi basitleştirin.
  * Tek bir proje dosyasını yönetmeniz gerektiğinden, çok hedefli projeler için kaynak dosya yönetimini basitleştirecek. Kaynak dosyaları eklendiğinde/kaldırırken, alternatifler bunları diğer projelerinizle el ile eşitlemeniz gerekir.
  * Tüketim için kolayca bir NuGet paketi oluşturma.
  * Derleyici yönergelerinin kullanımı aracılığıyla kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak tanır.

  *Desteklenmeyen senaryolar:*
  * Geliştiricilerin mevcut projeleri açmak için Visual Studio 2017 kullanmasını gerektirir. Visual Studio 'nun eski sürümlerini desteklemek için, [Proje dosyalarınızın farklı klasörlerde tutulması](#support-vs) daha iyi bir seçenektir.

* <a name="support-vs"></a>[**Mevcut projeleri ve yeni .NET Core projelerini ayrı tutun**](#keep-existing-projects-and-create-a-net-core-project)

  *Bunun için uygun olan şey:*
  * Visual Studio 2017 olmayan geliştiriciler/katkıda bulunanlar için yükseltme yapmak zorunda kalmadan mevcut projelerde geliştirmeyi desteklemeye devam edebilirsiniz.
  * Mevcut projelerde yeni hatalar oluşturma olasılığını azaltmak, çünkü bu projelerde hiçbir kod karmaşıklığı gerekli değildir.

## <a name="example"></a>Örnek

Aşağıdaki depoyu göz önünde bulundurun:

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Aşağıda, mevcut projelerin kısıtlamalarına ve karmaşıklığına bağlı olarak bu depoya yönelik .NET Core desteği eklemenin çeşitli yolları açıklanmaktadır.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Mevcut projeleri çok hedefli bir .NET Core projesiyle değiştirme

Depoyu, var olan tüm *@no__t -1. csproj* dosyalarının kaldırıldığından ve birden çok çerçeveyi hedefleyen tek bir *@no__t -3. csproj* dosyası oluşturulacak şekilde yeniden düzenleyin. Tek bir proje farklı çerçeveler için derleyebildiğinden bu harika bir seçenektir. Ayrıca hedeflenen çerçeveye göre farklı derleme seçeneklerini ve bağımlılıklarını işlemek için de güç vardır.

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Notda yapılan değişiklikler:

* *Packages. config* ve *@no__t -2. csproj* ' u yeni bir [.NET Core *@no__t -5. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj)ile değiştirme. NuGet paketleri `<PackageReference> ItemGroup` ile belirtilir.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Mevcut projeleri tut ve bir .NET Core projesi oluştur

Eski çerçeveleri hedefleyen mevcut projeler varsa, bu projeleri dokunmadan bırakmak ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesi kullanmak isteyebilirsiniz.

![Farklı klasördeki mevcut projeyi içeren .NET Core projesi](./media/project-structure/separate-projects-same-source.png)

[**Kaynak kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Notda yapılan değişiklikler:

* .NET Core ve var olan projeler ayrı klasörlerde tutulur.
  * Projelerin ayrı klasörlerde tutulması, Visual Studio 2017 ' i yapmanızı zorunlu tutar. Yalnızca eski projeleri açan ayrı bir çözüm oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core taşıma belgeleri](index.md)
