---
title: Geçiş fikirleri
description: ASP.NET MVC 'den .NET Core 'a geçiş yapılıp yapılmayacağını ve nasıl geçirileceğiyle ilgili doğru kararı vermek için bir takımın bilmeleri gerekir mi?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 5dba4fd058f66cfc49cbd2161232df85110a28f7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105875"
---
# <a name="migration-considerations"></a>Geçiş fikirleri

En temel soru ekipleri, uygulamalarının .NET Core 'a taşıma işlemi, her zaman bağlantı noktası olması durumunda yanıt vermelidir mi? Bazı durumlarda, en iyi yol ileri, ASP.NET MVC ve/veya Web API 'SI kullanılarak .NET Framework kalır. Bu bölümde, .NET Core 'a geçmesinin anlamlı olmasının nedenleri ele alır. Bu bölümde ayrıca senaryolar ve .NET Framework üzerinde kalma için onay noktaları da dikkate alır.

## <a name="is-migration-to-net-core-appropriate"></a>.NET Core 'a doğru geçiş yapılsın mı?

.NET Core 'a geçmek isteyebileceğiniz bazı nedenlerden biriyle başlayalım. Çok az sayıda var, bu yüzden bu listeyi ayrıntılı olarak değerlendirin.

### <a name="cross-platform-support"></a>Platformlar arası destek

.NET Core üzerinde oluşturulan uygulamalar, gerçekten platformlar arası bir platformdur ve Windows, Linux ve macOS üzerinde çalışabilir. Yalnızca geliştiricileriniz istedikleri donanımı kullanamazlar, ancak uygulamanızı dilediğiniz yerde da barındırabilirsiniz. Örnekler, yerel IIS 'den bulutta veya Linux Docker kapsayıcılarından IoT cihazlarına kadar uzanır.

### <a name="performance-and-scalability"></a>Performans ve ölçeklenebilirlik

.NET Core ile oluşturulan uygulamalar [, her yerde bulunan en hızlı teknoloji yığınlarından birinde](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)çalışmaktadır. ASP.NET MVC Apps, özellikle de .NET Core 'da bulunan bazı yeni özelliklerden faydalanmak için, ASP.NET Core performans iyileştirmelerini sıklıkla görebilirler.

### <a name="cloud-native"></a>Bulutta yerel

Yukarıdaki nedenler ve diğerleri için, .NET Core Uygulamaları Bulut barındırma ortamlarında çalışmaya uygundur. Hafif ve hızlı, .NET Core uygulamaları Azure Uygulama Hizmetleri 'ne veya kapsayıcılarına dağıtılabilir ve anında sistem talebini karşılamak için gerektikçe yatay olarak ölçeklendirilir.

### <a name="maintainable"></a>Sürdürülebilir

Birçok uygulama için müşteri ve iş ihtiyaçlarını karşılamaya devam ederken, Teknik borç, uygulamanın daha pahalı olduğunu ve sürdürülmesi durumunda. ASP.NET Core uygulamalar, ASP.NET MVC uygulamalarından daha kolay bir şekilde test edilir, böylece yeniden düzenleme ve güvenle genişletme işlemlerini kolaylaştırır.

### <a name="modular"></a>Modüler

ASP.NET Core, bir Framework 'ün birinci sınıf parçası olarak NuGet paketleri kullanılarak modüler olur. .NET Core için oluşturulan uygulamalar bağımlılık ekleme işlemini destekler, bu da belirli bir ortam için her türlü uygulamalardan çözüm oluşturmaya kolay hale gelir. .NET Core ile mikro hizmetler oluşturmak, büyük uygulamaları daha küçük modüllere bölmek için ek seçenekler açan ASP.NET MVC ile IIS 'nin bağımlılığı ile daha kolaydır.

### <a name="modern"></a>Modern

Modern, etkin şekilde geliştirilmiş bir teknoloji yığınında kalmakta olan bir avantaj ana bilgisayarı vardır. Yeni özellikler ve C# dil özellikleri yalnızca .NET Core 'a eklenecektir. .NET Framework sürüm 4,8 ile son sürümü vardı ve 8 ' den fazla C# sürümü .NET Framework hedeflemiyor. ASP.NET MVC pek çok yıl boyunca Microsoft tarafından desteklenmeye devam ederken, en iyi ve en parlak .NET yazılım geliştiricileri, sunduğu tüm avantajları (yalnızca bazıları yukarıda özetlenmiştir) sayesinde daha modern .NET Core Framework 'ü kullanmaya devam eder. Geliştiricilere bir ASP.NET MVC uygulamasının bakımını yapma becerileri ile bulma, çevrimiçi eğitim ve sorun giderme yardımını bulmayla ilgili bir noktada daha fazla bilgi edinmeye başlayacaktır. Örneğin, ASP.NET MVC 5 hakkında çok sayıda yeni blog gönderisinin yazıldığı, ancak .NET 5,0 için çok fazla yazılmakta olsa da, örneğin.

.NET Core 'a geçiş yapmayı düşünmenin pek çok ilgi çekici nedeni vardır. bu kitapta bu kitabı okumaktan kaçının! Ancak bazı dezavantajları ve neden .NET Framework kalmasının daha mantıklı olabileceğini düşündüm.

## <a name="when-is-net-framework-appropriate"></a>Ne zaman uygunsa .NET Framework?

.NET Framework kalmak için en büyük neden, bir uygulamanın etkin geliştirme kapsamında olmaması ve yukarıda listelenen avantajlardan önemli ölçüde yararlanmamamadır. Bu durumda, uygulamanın taşıma maliyetine tabi olmak büyük olasılıkla iyi bir iş durumu yoktur. Uygulamanız avantajlı .NET Core tekliflerine yarar olabileceğinden, .NET Core 'da kullanılamayan belirli teknolojiler varsa .NET Framework devam etmeniz gerekebilir. Uygulama etki alanları, uzaktan Iletişim, kod erişim güvenliği (CAS), güvenlik saydamlığı ve dahil [.NET Core 'da kullanılamayan bazı .NET teknolojileri](../../core/porting/net-framework-tech-unavailable.md)vardır `System.EnterpriseServices` . Bu teknolojilerin kısa bir özeti ve bunların alternatifleri aşağıda verilmiştir. Daha ayrıntılı rehberlik için belgelerine bakın.

### <a name="application-domains"></a>Uygulama etki alanları

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve pahalı olabilir. Ek uygulama etki alanlarının oluşturulması desteklenmez ve gelecekte bu özelliği .NET Core 'a eklemek için herhangi bir plan yoktur. Kod yalıtımı için alternatif olarak ayrı süreçler veya kapsayıcılar kullanın.

### <a name="wcf"></a>WCF

Sunucu tarafı WCF, .NET Core 'da desteklenmez. .NET Core, WCF ana bilgisayarlarını değil, WCF istemcilerini destekler. Bu işlevselliği gerektiren uygulamaların, geçişin bir parçası olarak farklı bir iletişim teknolojisine (gRPC veya REST gibi) yükseltilmesi gerekir.

[.Net Foundation 'da kullanılabilen bir WCF istemci bağlantı noktası](../../core/dotnet-five.md#windows-communication-foundation)vardır. Bu, tamamen açık kaynak, platformlar arası ve Microsoft tarafından desteklenmektedir. Ayrıca *, Microsoft tarafından resmi olarak* desteklenmeyen bir topluluk destekli [corewcf projesi](https://github.com/CoreWCF/CoreWCF) de mevcuttur.

### <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan Iletişim, sorunlu bir mimari olarak tanımlandı. Bu, artık desteklenmeyen ilkeler arası iletişim için kullanılır. Ayrıca, uzaktan Iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerden dolayı .NET Remoting, .NET Core 'da desteklenmez ve ürün ekibi gelecekte BT için destek eklemeyi planlamamaz. .NET Core uygulamalarınızda uzaktan iletişimi değiştirmek için kullanabileceğiniz çeşitli alternatif mesajlaşma stratejileri ve uygulamaları vardır.

### <a name="code-access-security-cas-and-security-transparency"></a>Kod erişim güvenliği (CAS) ve güvenlik saydamlığı

Bu teknolojilerin hiçbiri .NET Core tarafından desteklenmez. Bunun yerine, işletim sistemi tarafından sağlanmış olan güvenlik sınırlarını kullanmaktır. Örneğin, sanallaştırma, kapsayıcılar veya Kullanıcı hesapları. Gerekli olan en az ayrıcalık kümesini kullanarak süreçler çalıştırın.

## <a name="references"></a>Başvurular

[.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../core/porting/net-framework-tech-unavailable.md)

>[!div class="step-by-step"]
>[Önceki](introduction.md) 
> [Sonraki](migrate-aspnet-core-2-1.md)
