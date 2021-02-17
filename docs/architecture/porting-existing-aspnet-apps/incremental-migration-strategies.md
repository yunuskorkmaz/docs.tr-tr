---
title: Artımlı geçiş stratejileri
description: Takım, büyük uygulamaları ASP.NET MVC 'den .NET Core 'a artımlı bir biçimde geçirmeye olanak sağlayacak olan stratejileri benimseyebilirler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f09504c2c20c9038c3bdaa13c6a0ac0438f684e7
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583017"
---
# <a name="strategies-for-migrating-incrementally"></a>Artımlı geçiş stratejileri

Büyük bir uygulamayı geçirmeye en büyük zorluk, işlemin daha küçük görevlere nasıl kesilmesini belirliyor. Uygulamayı kullanıcı arabirimi, veri erişimi, iş mantığı gibi yatay katmanlara bölmek veya uygulamayı ayrı, daha küçük uygulamalara bölmek dahil olmak üzere, bu amaçla uygulanabilecek birkaç strateji vardır. Başka bir strateji, uygulamanın bir kısmını veya tamamını, son .NET Core sürümü gibi farklı çerçeve sürümlerine yükseltmelidir. Kullanabileceğiniz bir yaklaşım, tek seferde bir yatay katman geçirmeye çalışmak yerine uygulamanın [Dikey dilimlerini](https://deviq.com/practices/vertical-slices) geçirmekdür. Bu farklı yaklaşımlardan her birini ele alalım.

Büyük bir ASP.NET 4,5 uygulamasını geçirme sınamasını göz önünde bulundurun. Bir yaklaşım, tüm uygulamayı doğrudan .NET Framework 4,5 ' den .NET Core 3,1 ' den geçirmeye yönelik bir yaklaşımdır. Ancak, bu yaklaşım, önemli olan iki çerçeve ve sürüm arasındaki her bir son değişiklik için hesaba sahip olmalıdır.

## <a name="migrating-layer-by-layer"></a>Katmana göre katman geçirme

.NET ekosistemine, farklı .NET çerçeveleri arasında birlikte çalışabilirliğine yardımcı olan bir son ekleme [.NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard). .NET Standard, kitaplıkların ortak API 'Ler kümesi üzerinde anlaşmaya varılmış olarak derlenmesini sağlar ve bu sayede herhangi bir .NET uygulamasında kullanılabilir. .NET Standard 2,0, en .NET Framework ve .NET Core uygulamaları tarafından kullanılan temel sınıf kitaplığı işlevlerinin çoğunu kapsadığından önemli. Ne yazık ki, .NET 'in .NET Standard 2,0 desteği olan en eski sürümü .NET Framework 4.6.1 ve bu, .NET Framework 4,8 ' de ilk yükseltmelere yönelik etkileyici bir seçim yapan birkaç güncelleştirme vardır.

Bir .NET Framework 4,5 sistem katmanını artımlı olarak yükseltmeye yönelik bir yaklaşım, öncelikle sınıf kitaplıklarını .NET Framework 4,8 ' e güncelleştirmedir. Ardından, bu kitaplıkları .NET Standard sınıf kitaplıkları olacak şekilde değiştirin. Gerekirse, Çoklu hedefleme ve koşullu derleme kullanın. Bu adım, uygulama bağımlılıklarının .NET Framework gerektirdiği ve .NET Standard ve .NET Core kullanımı kolay bir şekilde doğrudan bağlantı geçirebileceği senaryolarda yararlı olabilir. .NET Framework kitaplıkları ASP.NET Core 2,1 uygulamaları tarafından tüketilebilmesi için bir sonraki adım, uygulamanın Web işlevselliğinin bazılarını veya tümünü ASP.NET Core 2,1 ' e ( [önceki bölümde](choose-net-core-version.md)açıklandığı gibi) geçirmelidir.

Uygulama ASP.NET Core 2,1 ' de çalışmaya başladıktan sonra, yalıtım ASP.NET Core 3,1 ' e geçişi nispeten basittir. Bu adım sırasında en olası zorluk, .NET Core ve büyük olasılıkla daha yüksek .NET Standard sürümleri desteklemek için uyumsuz bağımlılıkları güncelleştirmedir. Yalnızca .NET Framework kitaplıklarında sorunlu bağımlılıkları olmayan uygulamalarda, ASP.NET Core 2,1 ' e yükseltmeniz çok neden olabilir. ASP.NET Core 3,1 ' ye doğrudan taşıma daha anlamlı hale gelir ve daha az çaba gerektirir.

Uygulamanın .NET Core 3,1 ' de çalıştırıldığı zamana göre, geçerli .NET 5,0 sürümüne geçiş oldukça düşüktür. İşlem öncelikle proje dosyalarınızın hedef çerçevesini ve bunlarla ilişkili NuGet paketi bağımlılıklarını güncellemeyi içerir. [Göz önünde bulundurmanız gereken](/dotnet/core/compatibility/3.1-5.0)birkaç önemli değişiklik olsa da, çoğu uygulama .net Core 3,1 ' den .NET 5,0 ' e geçmek için önemli değişiklikler gerektirmez. [.NET Core 3,1 ve .net 5,0 arasında seçim](choose-net-core-version.md)yaparken birincil karar verme faktörü büyük olasılıkla destek olabilir.

## <a name="migrating-slice-by-slice"></a>Dilimi dilimle geçirme

Geçişe yönelik başka bir yaklaşım ise dikey işlev dilimlerini tanımlamak ve bunları hedef platforma tek tek geçirmek olacaktır. İlk adım, yeni bir ASP.NET Core 3,1 veya 5 uygulaması oluşturmaktır. Sonra, önce geçirilecek tek sayfayı veya API uç noktasını bir kez daha belirlemelisiniz. ASP.NET Core uygulamasında bu yolu desteklemek için yalnızca gerekli işlevleri oluşturun. Daha sonra, bu sayfalara veya uç noktalara yönelik istekleri ASP.NET uygulaması yerine yeni uygulamaya göndermeye başlamak için HTTP yeniden yazma ve/veya ters proxy kullanın.

Bu stratejiyi IIS kullanarak izlemeye yönelik bazı özel yönergeler [, Bölüm 5, dağıtım senaryolarında](deployment-scenarios-md)ele alınmıştır.

## <a name="references"></a>Başvurular

- [.NET Standard nedir?](https://dotnet.microsoft.com/platform/dotnet-standard)
- [.NET 5 tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-5/)
- [ASP.NET Core 3,1 ' den 5,0 ' e geçiş yapın](https://docs.microsoft.com/aspnet/core/migration/31-to-50)

>[!div class="step-by-step"]
>[Önceki](choose-net-core-version.md) 
> [Sonraki](migrate-web-forms.md)
