---
title: .NET Framework ve .NET Core için projeler düzenleyin
description: Çözümlerini .NET Framework ve .NET Core'a karşı yan yana derlemek isteyen proje sahiplerine yardımcı olun.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777328"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Projenizi hem .NET Framework hem de .NET Core'u destekleyecek şekilde düzenleyin

Hem .NET Framework hem de .NET Core için yan yana derleyen bir çözüm oluşturabilirsiniz. Bu makalede, bu hedefe ulaşmanıza yardımcı olmak için çeşitli proje organizasyonu seçenekleri kapsar. Proje düzeninizi .NET Core ile nasıl ayarladığınıza karar verirken göz önünde bulundurmanız gereken bazı tipik senaryolar aşağıda verilmiştir. Liste istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik belirleyin.

- [**Mevcut projeleri ve .NET Core projelerini tek projelerde birleştirin**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Bu ne için iyidir:*
  - Her biri farklı bir .NET Framework sürümünü veya platformunu hedefleyen birden çok proje yerine tek bir proje derleyerek yapı işleminizi kolaylaştırır.
  - Tek bir proje dosyalarını yönetmeniz gerektiğinden, çok hedefli projeler için kaynak dosya yönetimini basitleştirir. Kaynak dosyaları eklerken veya kaldırırken, alternatifler bunları diğer projelerinizle el ile eşitlemenizi gerektirir.
  - Kolayca tüketim için bir NuGet paketi oluşturun.
  - Derleyici yönergeleri ni kullanarak kitaplıklarınızda belirli bir .NET Framework sürümü için kod yazmanızı sağlar.

  *Desteklenmeyen senaryolar:*
  - Geliştiricilerin mevcut projeleri açmak için Visual Studio 2017 veya sonraki bir sürümü kullanmalarını gerektirir. Visual Studio'nun eski sürümlerini desteklemek için [proje dosyalarınızı farklı klasörlerde tutmak](#support-vs) daha iyi bir seçenektir.

- <a name="support-vs"></a>[**Mevcut projeleri ve yeni .NET Core projelerini ayrı tutun**](#keep-existing-projects-and-create-a-net-core-project)

  *Bu ne için iyidir:*
  - Visual Studio 2017 veya daha sonraki sürümü olmayan geliştiriciler ve katkıda bulunanlar için mevcut projelerin geliştirilmesini destekler.
  - Bu projelerde kod karmaşası gerekmediği için varolan projelerde yeni hata oluşturma olasılığını azaltır.

## <a name="example"></a>Örnek

Aşağıdaki depoyu göz önünde bulundurun:

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[**Kaynak Kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Aşağıdaki, varolan projelerin kısıtlamalarına ve karmaşıklığına bağlı olarak bu depo için .NET Core için destek eklemenin çeşitli yollarını açıklamaktadır.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Varolan projeleri çok hedefli bir .NET Core projesiyle değiştirme

Depoyu, varolan * \*.csproj* dosyalarının kaldırılacak şekilde yeniden düzenleyin ve birden çok çerçeveyi hedefleyen tek * \*bir .csproj* dosyası oluşturulur. Tek bir proje farklı çerçeveler için derlemek mümkün olduğundan, bu harika bir seçenektir. Ayrıca, hedeflenen çerçeve başına farklı derleme seçeneklerini ve bağımlılıkları işleme gücüne de sahiptir.

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[**Kaynak Kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Not değişiklikleri şunlardır:

- *Packages.config* ve * \*.csproj'un* yeni bir [.NET Core * \*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj)ile değiştirilmesi. NuGet paketleri ile `<PackageReference> ItemGroup`belirtilir.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Varolan projeleri koruyun ve bir .NET Core projesi oluşturun

Eski çerçeveleri hedefleyen varolan projeler varsa, bu projeleri el değmemiş olarak bırakmak ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesi kullanmak isteyebilirsiniz.

![.NET Core projesi farklı klasörde mevcut proje ile](./media/project-structure/separate-projects-same-source.png)

[**Kaynak Kodu**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

.NET Core ve varolan projeler ayrı klasörlerde tutulur. Projeleri ayrı klasörlerde tutmak, Visual Studio 2017 veya sonraki sürümlerine sahip olmaya zorlamanızı önler. Yalnızca eski projeleri açan ayrı bir çözüm oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek taşıma belgeleri](index.md)
