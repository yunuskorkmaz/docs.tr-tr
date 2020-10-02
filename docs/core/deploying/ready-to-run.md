---
title: ReadyToRun dağıtımına genel bakış
description: .NET 5 ve .NET Core 3,0 ve üzeri ile uygulamanızı yayımlamalarından bir parçası olarak, ReadyToRun dağıtımlarının ne olduğunu ve bu uygulamayı kullanmayı düşünmek zorunda olduğunu öğrenin.
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: b4052a0c0f4ed9f6cfd273abe5ef45d018bd0ae0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654965"
---
# <a name="readytorun-compilation"></a>ReadyToRun derlemesi

.NET uygulama başlangıç süresi ve gecikme süresi, uygulama derlemeleriniz ReadyToRun (R2R) biçimi olarak derlenerek artırılabilir. R2R, bir süre öncesi (AOT) derleme biçimidir.

R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir. İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir. Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür. R2R yalnızca Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir uygulama yayımladığınızda kullanılabilir.

Projenizi ReadyToRun olarak derlemek için, uygulamanın PublishReadyToRun özelliği true olarak ayarlanmış şekilde yayımlanması gerekir.

Uygulamanızı ReadyToRun olarak yayımlamanın iki yolu vardır:

01. PublishReadyToRun bayrağını doğrudan dotnet publish komutuna belirtin. Ayrıntılar için [DotNet Publish](../tools/dotnet-publish.md) bakın.

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. Projede özelliği belirtin

    - `<PublishReadyToRun>`Ayarı projenize ekleyin.

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - Uygulamayı özel parametre olmadan yayımlayın.

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a>ReadyToRun özelliğini kullanmanın etkileri

Güncel derleme, uygulama performansı üzerinde karmaşık performans etkilerine sahiptir ve tahmin edilmesi zor olabilir. Genel olarak, bir derlemenin boyutu iki ila üç kat daha büyük olacak şekilde artar. Dosyanın fiziksel boyutundaki bu artış, derlemeyi diskten yükleme performansını azaltabilir ve işlemin çalışma kümesini artırabilir. Ancak, dönüş sırasında çalışma zamanında derlenen yöntemlerin sayısı genellikle önemli ölçüde azaltılır. Sonuç olarak, büyük miktarlarda kod kullanan uygulamaların, ReadyToRun 'ı etkinleştirmesinin büyük performans avantajları elde edilmesine neden olur. .NET çalışma zamanı kitaplıkları zaten ReadyToRun ile önceden derlenmiş olduğundan, az miktarda koda sahip uygulamalar, ReadyToRun 'ı etkinleştirmenin önemli bir geliştirmesini yaşmaz.

Burada açıklanan başlangıç geliştirmesi yalnızca uygulama başlatma için değil, aynı zamanda uygulamadaki herhangi bir kodun ilk kullanımı için de geçerlidir. Örneğin, ReadyToRun, bir ASP.NET uygulamasında Web API 'sinin ilk kullanımı için yanıt gecikmesini azaltmak üzere kullanılabilir.

### <a name="interaction-with-tiered-compilation"></a>Katmanlı derleme ile etkileşim

Oluşturulma Zamanı, JıT tarafından üretilen kod olarak en iyi duruma getirilmiştir. Bu sorunu gidermek için katmanlı derleme yaygın olarak kullanılan ReadyToRun yöntemlerini JıT tarafından oluşturulan yöntemlerle değiştirecektir.

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a>Önceden derlenmiş derlemeler kümesi nasıl seçilir?

SDK, uygulamayla dağıtılan derlemeleri önceden derler. Kendi içinde bulunan uygulamalar için, bu derleme kümesi Framework 'ü içerir. C++/CLı ikilileri, ReadyToRun derlemesi için uygun değildir.

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a>Nasıl önceden derlenecek yöntemler kümesi seçildi?

Derleyici, mümkün olduğunca çok metodu önceden derlemeye çalışır. Ancak, ReadyToRun özelliğinin kullanılması beklenmediğinden, JıT 'in yürütülmesini engellemesine neden olur.

Bu nedenlerden bazıları şunlar olabilir ancak bunlarla sınırlı değildir:

- Ayrı derlemelerde tanımlanmış genel türlerin kullanımı
- Yerel kodla birlikte çalışma
- Derleyicinin bir hedef makinede kullanımı kanıtlayamadığını donanım iç bilgileri kullanımı
- Belirli olağandışı Il desenleri
- Yansıma veya LINQ aracılığıyla dinamik yöntem oluşturma

## <a name="cross-platformarchitecture-restrictions"></a>Platformlar arası/mimari kısıtlamaları

Bazı SDK platformları için, ReadyToRun derleyicisi diğer hedef platformlar için çapraz derlenebilecek bir derlemedir. Desteklenen derleme hedefleri aşağıdaki tabloda açıklanmıştır.

| SDK Platformu | Desteklenen hedef platformlar |
| ------------ | --------------------------- |
| Windows X64  | Windows x86, Windows x64, Windows ARM32, Windows ARM64 |
| Windows x86  | Windows x86, Windows ARM32 |
| Linux X64    | Linux x86, Linux x64, Linux ARM32, Linux ARM64 |
| Linux ARM32  | Linux ARM32 |
| Linux ARM64  | Linux ARM64 |
| macOS x64    | macOS x64 |
