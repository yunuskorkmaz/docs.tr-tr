---
title: ".NET Core taşıma -, üçüncü taraf taraf bağımlılıkları analiz etme"
description: ".NET Core taşıma - üçüncü taraf bağımlılıkları analiz etme"
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>.NET Core taşıma -, üçüncü taraf taraf bağımlılıkları analiz etme

Taşıma işleminde ilk adım, üçüncü taraf bağımlılıkları anlamaktır.  Hangisinin, varsa, verme henüz .NET Core üzerinde çalıştırın ve hangi .NET Core üzerinde çalıştırmayın olanlar için yedek bir plan geliştirin tahmin gerekir.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede varsayacak Windows ve Visual Studio kullanarak ve .NET Framework bugün çalışan koduna sahip.

## <a name="analyzing-nuget-packages"></a>NuGet paketleri analiz etme

Taşınabilirlik için NuGet paketleri analiz etme çok kolaydır.  Bir NuGet paketi kendisini platforma özgü derlemeleri içeren klasör kümesi, tüm yapmanız gereken olmadığından bir .NET Core derleme içeren bir klasör olup olmadığını denetleyin.

NuGet paketi klasörleri inceleyerek ile kolay [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı.  Bunun nasıl yapılacağı aşağıda verilmiştir.

1. Karşıdan yükleyip NuGet paketi Gezgini'ni açın.
2. "Çevrimiçi akış açık paketinden"'i tıklatın.
3. Paketin adını arayın.
4. Sağ taraftaki "LIB" klasörünü genişletin ve klasör adları bakın.

Bir paketi üzerinde destekler de görebilirsiniz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** o paket sayfasının bölümünde.

Her iki durumda da, bir klasör veya giriş arayın gerekir [nuget.org](https://www.nuget.org/) aşağıdaki adlarının herhangi biri ile:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Hedef Framework adlar (hangi sürümlerine eşleme TFM) bunlar [.NET standart](../../standard/net-standard.md) ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.  Unutmayın `netcoreapp1.0`, uyumlu iken, uygulamalar ve değil kitaplıkları içindir.  Olmasına karşın, bir kitaplık kullanılarak ile yanlış bir şey `netcoreapp1.0`-bağlı olarak, bu kitaplık için herhangi bir şey amaçlanmamış olabilir *diğer* diğer tüketimi daha `netcoreapp1.0` uygulamalar.

Uyumlu olabilir .NET Core yayın öncesi sürümlerini kullanılan bazı eski TFMs vardır:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

**Bu büyük olasılıkla kodunuzu ile çalışır durumdayken uyumluluk garantisi yoktur**.  Bu TFMs paketlerle yayın öncesi .NET Core paketlerle oluşturulmuştur.  Zaman (veya varsa) not edin böyle paketleri güncel olmasını `netstandard`-tabanlı.

> [!NOTE]
> Geleneksel PCL veya yayın öncesi .NET Core hedef hedefleme paketini kullanmak için kullanmanız gerekir `imports` yönergesini, `project.json` dosya.

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet paket bağımlılığı .NET Core üzerinde çalıştırdığınızda değil yapmanız gerekenler

Üzerinde bağımlı bir NuGet paketi .NET Core üzerinde çalışmaz, yapabileceğiniz birkaç şey vardır.

1. Proje açık bir kaynaktır ve Github'da gibi herhangi bir yerde barındırılan, developer(s) doğrudan devreye.
2. Yazarın doğrudan üzerinde başvurabilirsiniz [nuget.org](https://www.nuget.org/) paketi için arama ve paketin sayfasının sol tarafındaki "sahipleri başvurun" tıklatarak.
3. Kullanmakta olduğunuz paket gibi aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.
4. Paket kendiniz yapmakta olduğu için kod yazma girişiminde bulunabilir.
5. En az işlevselliği, uygulamanızın değiştirerek paket bağımlılığını ortadan paket uyumlu bir sürümü kullanılabilir duruma gelinceye kadar.

Lütfen açık kaynaklı proje maintainers ve NuGet paketi yayıncıları genellikle çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı daytime iş sahip katkıda gönüllüsü olduğunu unutmayın. Ulaşmak, .NET Core desteği hakkında isteyen önce pozitif deyimiyle Kitaplığı hakkında başlayabilir.

Yukarıdakilerden herhangi biri ile sorununuzu yapamıyorsanız, .NET Core bağlantı noktasına daha sonraki bir tarihte zorunda kalabilirsiniz.

.NET ekibi hangi kitaplıkları ile .NET Core sonraki desteklemek en önemli olan bilmek ister misiniz? Ayrıca bize e-posta gönderebilirsiniz dotnet@microsoft.com kullanmak istediğiniz kitaplıklar hakkında.

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>NuGet paketlerini bulunmayan bağımlılıklara analiz etme

Dosya sistemi DLL'de gibi bir NuGet paketi olmayan bir bağımlılık olabilir.  Bu bağımlılık taşınabilirlik belirlemek için tek yolu çalıştırmaktır [ApiPort aracı](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).

## <a name="next-steps"></a>Sonraki adımlar

Kitaplığa bağlantı noktası oluşturma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).
