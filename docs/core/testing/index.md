---
title: .NET 'te test etme
description: Bu makalede, .NET 'te test için kavramların, terminolojinin ve araçların test edilmesine ilişkin kısa bir genel bakış sunulmaktadır.
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 36e88cc059447a98931593e0535c70cbc92a2cf4
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223478"
---
# <a name="testing-in-net"></a>.NET 'te test etme

Bu makale test kavramını tanıtır ve farklı test türlerinin kodu doğrulamak için nasıl kullanılabileceğini gösterir. .Net [CLI](#net-cli) veya [Tümleşik geliştirme ortamları (IDN 'ler)](#ide)gibi .NET uygulamalarını test etmek için kullanabileceğiniz çeşitli araçlar vardır.

## <a name="test-types"></a>Test türleri

Otomatikleştirilmiş testlerin olması, uygulama kodunun yazarların yaptığı şeyleri yaptığını sağlamak için harika bir yoldur. Bu makalede birim testleri, tümleştirme testleri ve yük testleri ele alınmaktadır.

### <a name="unit-tests"></a>Birim testleri

*Birim testi* , "iş birimi" olarak da bilinen ayrı yazılım bileşenlerini veya yöntemlerini uygulayan bir sınamadır. Birim testleri yalnızca geliştiricinin denetimindeki kodu test etmelidir. Altyapı sorunlarını test etmez. Altyapı sorunları veritabanları, dosya sistemleri ve ağ kaynaklarıyla etkileşimde bulunur.

Birim testleri oluşturma hakkında daha fazla bilgi için bkz. [test araçları](#testing-tools).

### <a name="integration-tests"></a>Tümleştirme testleri

*Tümleştirme testi* , iki veya daha fazla yazılım bileşeninin birlikte çalışmasını sağlayan, "tümleştirme" olarak da bilinen bir birim testinden farklıdır. Bu testler, test edilen sistemin daha geniş bir yelpazesi üzerinde çalışır, ancak birim testleri ayrı bileşenlere odaklanmaktadır. Genellikle, tümleştirme testlerine altyapı sorunları dahildir.

### <a name="load-tests"></a>Yük testleri

Bir sistemin belirtilen yükü işleyemeyeceğini, örneğin bir uygulamayı kullanan eşzamanlı kullanıcı sayısını ve uygulamanın etkileşimleri boyutlandırılabilir işleme yeteneğini tespit etmek için bir *Yük testi* amaçlar. Web uygulamalarının yük testi hakkında daha fazla bilgi için bkz. [ASP.NET Core yük/stres testi](/aspnet/core/test/load-tests).

## <a name="test-considerations"></a>Test değerlendirmeleri

Testleri yazmak için [en iyi uygulamaları](unit-testing-best-practices.md) aklınızda bulundurun. Örneğin, [test odaklı geliştirme (TDD)](https://deviq.com/test-driven-development) , bir birim testinin denetlenecek koddan önce yazıldığı bir birimdir. TDD, bir kitabı yazmadan önce bir ana hat oluşturmaya benzer. Geliştiricilerin daha basit, daha okunabilir ve verimli bir kod yazmasına yardımcı olmak için tasarlanmıştır.

## <a name="testing-tools"></a>Test araçları

.Net, çok dilli bir geliştirme platformudur ve [C#](../../csharp/index.yml), [F #](../../fsharp/index.yml)ve [Visual Basic](../../visual-basic/index.yml)için çeşitli test türleri yazabilirsiniz. Bu dillerin her biri için çeşitli test çerçeveleri arasından seçim yapabilirsiniz.

### <a name="xunit"></a>xUnit

[xUnit](https://xunit.net) , .NET için ücretsiz, açık kaynaklı ve topluluk odaklı birim testi aracıdır. NUnit V2 özgün Inventor tarafından yazılan xUnit.net, birim testi .NET uygulamaları için en son teknolojiden oluşur. xUnit.net, ReSharper, CodeRush, TestDriven.NET ve [Xamarin](/apps/xamarin)ile birlikte kullanılabilir. [.Net Foundation](https://dotnetfoundation.org) 'ın bir projem ve bunların kullanım kuralları altında çalışır.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [C ile birim testi #](unit-testing-with-dotnet-test.md)
- [F ile birim testi #](unit-testing-fsharp-with-dotnet-test.md)
- [Visual Basic ile birim testi](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a>NUnit

[NUnit](https://nunit.org) , tüm .NET dilleri için bir birim testi çerçevesidir. Başlangıçta JUnit 'ten itibaren, geçerli üretim sürümü çok sayıda yeni özellik ve birçok .NET platformu için destek ile yeniden yazıldı. [.Net Foundation](https://dotnetfoundation.org)'ın bir projem.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [C ile birim testi #](unit-testing-with-nunit.md)
- [F ile birim testi #](unit-testing-fsharp-with-nunit.md)
- [Visual Basic ile birim testi](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a>MSTest

[MSTest](https://github.com/Microsoft/testfx-docs) , tüm .NET dilleri için Microsoft Test çerçevesidir. Genişletilebilir ve hem .NET CLı hem de Visual Studio ile çalışmaktadır. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [C ile birim testi #](unit-testing-with-mstest.md)
- [F ile birim testi #](unit-testing-fsharp-with-mstest.md)
- [Visual Basic ile birim testi](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a>.NET CLı

[.Net CLI](../tools/index.md)'den, [DotNet test](../tools/dotnet-test.md) komutuyla bir çözüm birim testlerini çalıştırabilirsiniz. .NET CLı, [Tümleşik geliştirme ortamları (IDN 'ler)](#ide) Kullanıcı arabirimleri aracılığıyla kullanılabilir hale gelen işlevselliğin çoğunu kullanıma sunar. .NET CLı, platformlar arası ve sürekli tümleştirme ve teslim işlem hatlarının bir parçası olarak kullanılabilir. .NET CLı, ortak görevleri otomatikleştirmek için komut dosyalı işlemlerle birlikte kullanılır.

### <a name="ide"></a>IDE

Visual Studio, Mac için Visual Studio veya Visual Studio Code kullanıp kullansanız, test işlevselliği için grafik kullanıcı arabirimleri vardır. CLı tarafından kullanılabilecek daha fazla özellik vardır, örneğin [Live Unit Testing](/visualstudio/test/live-unit-testing). Daha fazla bilgi için bkz. [Visual Studio ile testleri dahil etme ve hariç tutma](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).

## <a name="see-also"></a>Ayrıca bkz.

Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

- [.NET ile birim testi en iyi uygulamaları](unit-testing-best-practices.md)
- [ASP.NET Core tümleştirme testleri](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [Seçmeli birim testleri çalıştırma](selective-unit-tests.md)
- [Birim testi için kod kapsamını kullanma](unit-testing-code-coverage.md)
