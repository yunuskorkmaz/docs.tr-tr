---
title: Artımlı geçiş stratejileri
description: Takım, büyük uygulamaları ASP.NET MVC 'den .NET Core 'a artımlı bir biçimde geçirmeye olanak sağlayacak olan stratejileri benimseyebilirler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 615d2a853b698bfc752c3baf36f31ab2a4f2bab8
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122891"
---
# <a name="strategies-for-migrating-incrementally"></a>Artımlı geçiş stratejileri

Büyük bir uygulamayı geçirmeye en büyük zorluk, işlemin daha küçük görevlere nasıl kesilmesini belirliyor. Uygulamayı kullanıcı arabirimi, veri erişimi, iş mantığı gibi yatay katmanlara bölmek veya uygulamayı ayrı, daha küçük uygulamalara bölmek dahil olmak üzere, bu amaçla uygulanabilecek birkaç strateji vardır. Başka bir strateji, uygulamanın bir kısmını veya tamamını, son .NET Core sürümü gibi farklı çerçeve sürümlerine yükseltmelidir. Kullanabileceğiniz bir yaklaşım, tek seferde bir yatay katman geçirmeye çalışmak yerine uygulamanın [Dikey dilimlerini](https://deviq.com/practices/vertical-slices) geçirmekdür. Bu farklı yaklaşımlardan her birini ele alalım.

## <a name="migrating-slice-by-slice"></a>Dilimi dilimle geçirme

Geçiş için başarılı bir yaklaşım, dikey işlevlerin düşey dilimlerinin tanımlanması ve bunları hedef platforma tek tek geçirkullanmaktır. İlk adım, yeni bir ASP.NET Core 3,1 veya 5 uygulaması oluşturmaktır. Sonra, önce geçirilecek tek sayfayı veya API uç noktasını bir kez daha belirlemelisiniz. ASP.NET Core uygulamasında bu yolu desteklemek için yalnızca gerekli işlevleri oluşturun. Daha sonra, bu sayfalara veya uç noktalara yönelik istekleri ASP.NET uygulaması yerine yeni uygulamaya göndermeye başlamak için HTTP yeniden yazma ve/veya ters proxy kullanın. Bu yaklaşım, API projelerine uygundur, ancak pek çok MVC uygulaması için de çalışabilir.

Dilimi dilime geçirirken, tek tek API uç noktası veya istenen yolun tüm yığını yeni proje veya çözümde yeniden oluşturulur. Genellikle çok sayıda projenin oluşturulması ve veri erişimi ve çözüm organizasyonu hakkında kararlar olması gerektiğinden, bu dilim genellikle en fazla çaba gerektirir. İlk dilimin işlevselliği mevcut uygulamayı yansıtdıktan sonra dağıtılabilir ve var olan uygulama buna yönlendirebilir ya da yalnızca kaldırılabilir. Bu yaklaşım daha sonra tüm uygulama yeni yapıya alınana kadar yinelenir.

Bu stratejiyi IIS kullanarak izlemeye yönelik bazı özel yönergeler [, Bölüm 5, dağıtım senaryolarında](deployment-scenarios.md)ele alınmıştır.

## <a name="migrating-layer-by-layer"></a>Katmana göre katman geçirme

Büyük bir ASP.NET 4,5 uygulamasını geçirme sınamasını göz önünde bulundurun. Bir yaklaşım, tüm uygulamayı doğrudan .NET Framework 4,5 ' den .NET Core 3,1 ' den geçirmeye yönelik bir yaklaşımdır. Ancak, bu yaklaşım, önemli olan iki çerçeve ve sürüm arasındaki her bir son değişiklik için hesaba sahip olmalıdır. Aynı anda tek bir projede bu çalışmanın gerçekleştirilmesi, tüm çözümün aynı anda taşınması gerekmemesi için bir dizi Adımlama sağlar.

.NET ekosistemine, farklı .NET çerçeveleri arasında birlikte çalışabilirliğine yardımcı olan bir son ekleme [.NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard). .NET Standard, kitaplıkların ortak API 'Ler kümesi üzerinde anlaşmaya varılmış olarak derlenmesini sağlar ve bu sayede herhangi bir .NET uygulamasında kullanılabilir. .NET Standard 2,0, en .NET Framework ve .NET Core uygulamaları tarafından kullanılan temel sınıf kitaplığı işlevlerinin çoğunu kapsadığından önemli. Ne yazık ki, .NET 'in .NET Standard 2,0 desteği olan en eski sürümü .NET Framework 4.6.1 ve bu, .NET Framework 4,8 ' de ilk yükseltmelere yönelik etkileyici bir seçim yapan birkaç güncelleştirme vardır.

.NET Framework 4,5 sistem katmanını artımlı olarak yükseltmeye yönelik bir yaklaşım, öncelikle sınıf kitaplığı bağımlılıklarını .NET Framework 4,8 ' e güncelleştirmedir. Ardından, bu kitaplıkları .NET Standard sınıf kitaplıkları olacak şekilde değiştirin. Gerekirse, Çoklu hedefleme ve koşullu derleme kullanın. Bu adım, uygulama bağımlılıklarının .NET Framework gerektirdiği ve .NET Standard ve .NET Core kullanımı kolay bir şekilde doğrudan bağlantı geçirebileceği senaryolarda yararlı olabilir. .NET Framework kitaplıkları ASP.NET Core 2,1 uygulamaları tarafından tüketilebilmesi için bir sonraki adım, uygulamanın Web işlevselliğinin bazılarını veya tümünü ASP.NET Core 2,1 ' e ( [önceki bölümde](choose-net-core-version.md)açıklandığı gibi) geçirmelidir. Bu, düşük düzey sınıf kitaplığı bağımlılıklarından başlayıp Web uygulaması giriş noktasına çalışarak bir "alt yukarı" yaklaşımıdır.

Uygulama ASP.NET Core 2,1 ' de çalışmaya başladıktan sonra, yalıtım ASP.NET Core 3,1 ' e geçişi nispeten basittir. Bu adım sırasında en olası zorluk, .NET Core ve büyük olasılıkla daha yüksek .NET Standard sürümleri desteklemek için uyumsuz bağımlılıkları güncelleştirmedir. Yalnızca .NET Framework kitaplıklarında sorunlu bağımlılıkları olmayan uygulamalarda, ASP.NET Core 2,1 ' e yükseltmeniz çok neden olabilir. ASP.NET Core 3,1 ' ye doğrudan taşıma daha anlamlı hale gelir ve daha az çaba gerektirir.

Uygulamanın .NET Core 3,1 ' de çalıştırıldığı zamana göre, geçerli .NET 5 sürümüne geçiş oldukça düşüktür. İşlem öncelikle proje dosyalarınızın hedef çerçevesini ve bunlarla ilişkili NuGet paketi bağımlılıklarını güncellemeyi içerir. [Göz önünde bulundurulması gereken](../../core/compatibility/5.0.md)birkaç önemli değişiklik olsa da, çoğu uygulama .net Core 3,1 ' den .NET 5 ' e geçmek için önemli değişiklikler gerektirmez. [.NET Core 3,1 ve .NET 5 arasında seçim](choose-net-core-version.md)yaparken birincil karar verme faktörü büyük olasılıkla destek olabilir.

Bir "alt yukarı" yaklaşımı yerine, başka bir alternatif de Web uygulamasıyla (veya tüm çözümle birlikte) başlamak ve yükseltmeye yardımcı olması için otomatikleştirilmiş bir araç kullanmaktır. [.NET Yükseltme Yardımcısı aracı](https://aka.ms/dotnet-upgrade-assistant) , .NET Framework uygulamalarını .NET Core/.NET 5 ' e yükseltmeye yardımcı olmak için kullanılabilir. Proje dosyası biçimini değiştirme, uygun hedef çerçeveleri ayarlama, NuGet bağımlılıklarını güncelleştirme ve daha fazlası gibi uygulamaları yükseltmeyle ilgili birçok ortak görevi otomatikleştirir.

Bir "alt yukarı" yaklaşımı yerine, başka bir alternatif de Web uygulamasıyla (veya tüm çözümle birlikte) başlamak ve yükseltmeye yardımcı olması için otomatikleştirilmiş bir araç kullanmaktır. [.NET Yükseltme Yardımcısı aracı](https://aka.ms/dotnet-upgrade-assistant) , .NET Framework uygulamalarını .NET Core/.NET 5 ' e yükseltmeye yardımcı olmak için kullanılabilir. Proje dosyası biçimini değiştirme, uygun hedef çerçeveleri ayarlama, NuGet bağımlılıklarını güncelleştirme ve daha fazlası gibi uygulamaları yükseltmeyle ilgili birçok ortak görevi otomatikleştirir.

## <a name="references"></a>Başvurular

- [.NET Standard nedir?](https://dotnet.microsoft.com/platform/dotnet-standard)
- [.NET 5 tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-5/)
- [ASP.NET Core 3,1 ' den 5,0 ' e geçiş yapın](/aspnet/core/migration/31-to-50)
- [.NET Yükseltme Yardımcısı aracı](https://aka.ms/dotnet-upgrade-assistant)

>[!div class="step-by-step"]
>[Önceki](choose-net-core-version.md) 
> [Sonraki](migrate-web-forms.md)
