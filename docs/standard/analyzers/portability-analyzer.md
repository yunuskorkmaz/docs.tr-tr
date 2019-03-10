---
title: .NET Portability Analyzer - .NET
description: '.NET Core, .NET standart, UWP ve Xamarin de dahil olmak üzere çeşitli .NET uygulamaları arasında nasıl taşınabilir kodunuz: değerlendirilecek .NET Portability Analyzer aracını kullanmayı öğrenin.'
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: bd92e39a7b53e2807aff687f6dfbf71be34a506d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717654"
---
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

Çok platformlu Kitaplıklarınızı mu oluşturmak istiyorsunuz? Uygulamanız diğer .NET uygulamaları ve .NET Core, .NET standart, UWP ve Xamarin iOS, Android ve Mac için dahil olmak üzere ile uyumlu hale getirmek için ne kadar iş gereklidir görmek ister misiniz? [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) nasıl programınızı .NET uygulamaları arasında derlemeler analiz ederek esnektir üzerinde ayrıntılı bir rapor sağlayan bir araçtır. Taşınabilirlik Çözümleyicisi Visual Studio uzantısı ve bir konsol uygulaması olarak sunulur.

## <a name="new-targets"></a>Yeni hedefleri

* [.NET core](../../core/index.md): Modüler bir tasarım olan, yan yana artırdığını ve platformlar arası senaryolar hedefler. Yan yana diğer uygulamaları bozmadan yeni .NET Core sürümleri benimsemenizi sağlar.
* [ASP.NET Core](/aspnet/core):, bir modern web-böylece geliştiriciler avantajların vererek, .NET Core üzerine yapılandırılan altyapısıdır.
* [Evrensel Windows platformu](https://devblogs.microsoft.com/dotnet/net-native-performance/): .NET Native'nın statik derlemesi kullanarak x64 ve ARM makineleri üzerinde çalışan Windows Store uygulamalarınızın performansını geliştirin. 
* .NET core + uzantılar: WCF ve ASP.NET Core, FSharp ve Azure gibi .NET ekosistemindeki diğer API'lerin yanı sıra .NET Core API'ları içerir.
* .NET standard + uzantılar: WCF ve ASP.NET Core, FSharp ve Azure gibi diğer .NET ekosisteminin yanı sıra .NET standart API'ler de dahildir.

## <a name="how-to-use-portability-analyzer"></a>Taşınabilirlik Çözümleyicisi'ni kullanma

.NET Portability Analyzer'ı kullanmaya başlamak için öncelikle uzantısını indirip ihtiyacınız [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Visual Studio 2015 ve Visual Studio 2017 üzerinde çalışır. Visual Studio yapılandırma **Çözümle** > **taşınabilirlik Çözümleyicisi ayarları** ve uygulamanızın hedef platformlarını seçin.

![Taşınabilirlik ekran görüntüsü](./media/portability-analyzer/portability-screenshot.png)

Tüm projenizi çözümlemek için projenizde sağ **Çözüm Gezgini** seçip **analiz derleme taşınabilirlik**. Aksi takdirde, Git **Çözümle** menü ve select **analiz derleme taşınabilirlik**. Burada, projenizin yürütülebilir dosyası veya DLL'ı seçin.

![Taşınabilirlik Çözüm Gezgini](./media/portability-analyzer/portability-solution-explorer.png)

Analiz çalıştırdıktan sonra .NET taşınabilirlik raporunuzu görürsünüz. Yalnızca hedef platform tarafından desteklenmeyen türlerini listede görünür ve önerileri gözden geçirebilirsiniz **iletileri** sekmesinde **hata listesi**. Sorunlu alanları doğrudan da atlayabilirsiniz **iletileri** sekmesi.

![Taşınabilirlik raporu](./media/portability-analyzer/portability-report.png)

Visual Studio kullanmak istemiyor musunuz? Komut isteminden taşınabilirlik Çözümleyicisi'ni de kullanabilirsiniz. Hemen indirin [API Portability Analyzer](https://www.microsoft.com/download/details.aspx?id=42678).

*   Geçerli dizin analiz etmek için aşağıdaki komutu yazın: `\...\ApiPort.exe analyze -f .`
*   Belirli bir .dll dosyaları listesini analiz etmek için aşağıdaki komutu yazın: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

.NET taşınabilirlik raporunuzu bir Excel dosyası olarak kaydedildi (*.xlsx*) geçerli dizininizde. **Ayrıntıları** Excel çalışma kitabı sekmesi daha fazla bilgi içerir.

.NET Portability Analyzer hakkında daha fazla bilgi için ziyaret [GitHub belgeleri](https://github.com/Microsoft/dotnet-apiport#documentation) ve [bir kısa bakın .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) kanal 9 videosu.
