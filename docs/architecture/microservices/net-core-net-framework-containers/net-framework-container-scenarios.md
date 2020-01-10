---
title: Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker kapsayıcıları için .NET Framework seçme
ms.date: 01/07/2019
ms.openlocfilehash: 579e1a475b1ce96d98d7a2c521c1296e17b9f42e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740958"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?

.NET Core yeni uygulamalar ve uygulama desenleri için önemli avantajlar sağladığından, .NET Framework birçok mevcut senaryo için iyi bir seçenek olmaya devam edecektir.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Mevcut uygulamaları doğrudan bir Windows Server kapsayıcısına geçirme

Mikro hizmetler oluşturmasanız bile, yalnızca dağıtımı basitleştirmek için Docker kapsayıcılarını kullanmak isteyebilirsiniz. Örneğin, Docker ile DevOps iş akışınızı geliştirmek isteyebilirsiniz. kapsayıcılar, size daha iyi yalıtılmış test ortamları verebilir ve ayrıca bir üretim ortamına geçtiğinizde eksik bağımlılıklardan kaynaklanan dağıtım sorunlarını ortadan kaldırabilir. Bunlar gibi durumlarda, tek parçalı bir uygulama dağıtsanız bile, geçerli .NET Framework uygulamalarınız için Docker ve Windows kapsayıcıları kullanmak mantıklı olur.

Bu senaryo için çoğu durumda, mevcut uygulamalarınızı .NET Core 'a geçirmeniz gerekmez; geleneksel .NET Framework içeren Docker Kapsayıcıları kullanabilirsiniz. Ancak, ASP.NET Core ' de yeni bir hizmet yazma gibi, mevcut bir uygulamayı genişletmekle birlikte .NET Core kullanmak önerilen bir yaklaşımdır.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için mevcut olmayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanma

Üçüncü taraf kitaplıklar, .NET Core dahil olmak üzere tüm .NET türleri genelinde kod paylaşımına izin veren [.NET Standard](../../../standard/net-standard.md)hızla bir şekilde kabul eder. .NET Standard kitaplığı 2,0 ve farklı çerçeveler genelinde API Surface uyumluluğunun ötesinde büyük ölçüde daha büyük hale gelmiştir ve .NET Core 2. x uygulamaları ayrıca doğrudan mevcut .NET Framework kitaplıklarına başvurabilir (bkz. [.NET Framework 4.6.1 destekleme .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Ayrıca, Windows [Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md) windows üzerinde .NET Standard 2,0 için KULLANILABILIR olan API yüzeyini GENIŞLETMEK için kas-2017 ' de kullanıma sunulmuştur. Bu paket, Windows üzerinde çalıştırmak için çok sayıda kodu .NET Standard 2. x ' e yeniden derliyorsanız ve çok az değişiklikle.

Bununla birlikte, 2,0 ve .NET Core 2,1 ' den .NET Standard bu yana bu olağanüstü ilerlemeyi bile, bazı NuGet paketlerinin Windows 'un çalışması ve .NET Core 'u desteklememe gibi durumlar olabilir. Bu paketler uygulamanız için önemliyse, Windows kapsayıcılarında .NET Framework kullanmanız gerekir.

## <a name="using-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılamayan .NET teknolojilerini kullanma

Bazı .NET Framework teknolojileri .NET Core 'un geçerli sürümünde (Bu yazma itibariyle sürüm 2,2) kullanılamaz. Bazıları, daha sonraki .NET Core sürümlerinde (.NET Core 2. x) kullanılabilir, ancak diğerleri ise .NET Core tarafından hedeflenen yeni uygulama desenleri için uygulanmazlar ve hiçbir şekilde kullanılamayabilir.

Aşağıdaki listede .NET Core 2. x ' de kullanılamayan teknolojilerin çoğu gösterilmektedir:

- ASP.NET Web Forms. Bu teknoloji yalnızca .NET Framework kullanılabilir. Şu anda ASP.NET Web Forms .NET Core 'a getirmeye yönelik bir plan yoktur.

- WCF Hizmetleri. Bir [WCF-istemci kitaplığı](https://github.com/dotnet/wcf) , .net 2017 Core 'dan WCF Hizmetleri 'ni tüketmek için kullanılabilir olduğunda bıle, WCF sunucu uygulamasının yalnızca .NET Framework kullanılabilir. Bu senaryo, .NET Core 'un gelecek sürümleri için göz önünde bulundurulmalı, [Windows Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md)'ne dahil edilmesi Için bazı API 'ler bile vardır.

- İş akışı ile ilgili hizmetler. Windows Workflow Foundation (WF), Iş akışı hizmetleri (tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eski adıyla ADO.NET veri Hizmetleri) yalnızca .NET Framework kullanılabilir. Şu anda bunları .NET Core 'a getirmeye yönelik bir plan yoktur.

Resmi [.NET Core yol haritasında](https://github.com/aspnet/Home/wiki/Roadmap)listelenen teknolojilerin yanı sıra, diğer özellikler de .NET Core 'a eklenebilir. Tam liste için CoreFX GitHub sitesinde [bağlantı noktası](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) olarak etiketlenmiş öğelere bakın. Bu listede, Microsoft 'un bu bileşenleri .NET Core 'a getirmesinin bir taahhüdünü temsil etmediği ve öğelerin topluluklardan yalnızca istekleri yakaladığı unutulmamalıdır. Yukarıda listelenen bileşenlerden herhangi birini düşünüyorsanız, sesinizin duyabilmesi için GitHub 'daki tartışmalara katılımını düşünün. Bir şeyin eksik olduğunu düşünüyorsanız, lütfen [çalışma zamanı deposunda yeni bir sorun](https://github.com/dotnet/runtime/issues/new)bildirin.

.NET Core 3 ' ün (Bu yazma işlemi çalışır durumda olduğundan) çok sayıda mevcut .NET Framework API 'Leri için destek de dahil olmak üzere, bunlar masaüstü yönelimlidir ve şu anda kapsayıcı dünyada hiç kullanılmamaktadır.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>.NET Core desteklemeyen bir platform veya API kullanma

Bazı Microsoft veya üçüncü taraf platformları .NET Core ' u desteklemez. Örneğin, bazı Azure Hizmetleri, .NET Core üzerinde tüketim için henüz kullanılamayan bir SDK sağlar. Bu geçicidir çünkü tüm Azure hizmetleri sonunda .NET Core 'u kullanacaktır. Örneğin, [.NET Core Için Azure DocumentDB SDK 'sı](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) , 16 Kasım 2016 ' de önizleme olarak yayımlanmıştır, ancak artık kararlı bir sürüm olarak genel kullanıma sunulmuştur (GA).

Bu sırada, Azure 'daki herhangi bir platform veya hizmet, istemci API 'SI ile .NET Core 'u desteklemiyorsa, Azure hizmetindeki veya .NET Framework istemci SDK 'sindeki eşdeğer REST API de kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core kılavuzu** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **.NET Framework \ .NET Core 'A taşıma**
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Docker kılavuzundaki .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.Net bileşenlerine genel bakış** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Önceki](net-core-container-scenarios.md)
>[İleri](container-framework-choice-factors.md)
