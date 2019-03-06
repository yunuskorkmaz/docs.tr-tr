---
title: .NET bütünleştirilmiş kodu dosya biçimi
description: .NET uygulamaları ve kitaplıkları içerir ve açıklamak için kullanılan .NET derlemesi dosya biçimi hakkında bilgi edinin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 0bde31a004b1952be488569f89cfd3b129c82771
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369078"
---
# <a name="net-assembly-file-format"></a>.NET bütünleştirilmiş kodu dosya biçimi

.NET, tam olarak tanımlamak ve .NET programlarının içermesi için kullanılan bir ikili dosya biçimi - "assembly" - tanımlar. Derlemeleri, bağımlı tüm kitaplıkları yanı sıra programların kendileri için kullanılır. .NET programı ile diğer gerekli yapıt yok, uygun bir .NET uygulaması dışında bir veya daha fazla derlemeleri olarak çalıştırılabilir. İşletim sistemi API ' ları dahil olmak üzere yerel bağımlılıklar ayrı önemli olan ve bazen bu biçiminde (örneğin, WinRT) açıklanan olsa da .NET derleme biçim içinde yer almayan.

> Her bir CLI bileşeni bildirimleri, uygulamaları ve söz konusu bileşen için belirli başvuruları için meta verileri taşır. Bu nedenle, bileşen özgü meta veriler bileşen meta verileri adlandırılır ve sonuçta elde edilen bileşen – ECMA-335 I.9.1, bileşenler ve derlemelerin kendiliğinden açıklayıcı olmasını kabul edilir.

Biçim tam olarak belirtilen ve olarak standartlaştırılmış [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Tüm .NET derleyiciler ve çalışma zamanları şu biçimi kullanın. Belgelenmiş ve sık güncelleştirilmiş bir ikili biçimi varlığı birlikte çalışabilirlik için önemli bir avantajı (tartışmaya bir gereksinim) kaldırıldı. Biçim, 2005'te genel türler ve işlemci mimarisi uyum sağlamak için (.NET 2.0) son substantive şekilde güncelleştirildi.

CPU ve işletim sistemi belirsiz biçimindedir. Birçok yongaları ve CPU'yu hedef .NET uygulamaları bir parçası olarak kullanıldı. Biçim Windows miras olsa da tüm işletim sistemlerinde implementable. Tartışmasız en önemli dilediği işletim sistemi birlikte çalışabilirlik için çoğu değerleri endian biçiminde depolanır. Bu makine işaretçi boyutu (örneğin, 32-bit, 64-bit) için belirli bir benzeşim gerekli değildir.

.NET derleme de çok belirli bir programı veya kitaplık yapısı hakkında açıklayıcı biçimidir. Özel bir derlemenin iç bileşenleri tanımlayan: bütünleştirilmiş kod başvuruları ve tanımlanan türleri ve kendi iç yapısı. Araç veya API'lerden okuyabilir ve bu bilgileri görüntülemek için ya da programlı kararları vermek için işlem.

## <a name="format"></a>Biçimi

Windows üzerinde .NET ikili biçimi alan [PE dosyası](https://en.wikipedia.org/wiki/Portable_Executable) biçimi. Aslında, .NET sınıf kitaplıkları Windows PEs uyumlu olan ve Windows dinamik bağlantı kitaplıklarını (DLL'ler) veya uygulama yürütülebilir dosyaların (EXE'ler) ilk bakışta görünür. Windows geçici yerel yürütülebilir ikili dosyaları ve burada bazı aynı işleme (örneğin, işletim sistemi yükleme, PE Araçlar) edinin üzerinde çok kullanışlı bir özellik budur.

![Derleme üstbilgileri](../media/assembly-format/assembly-headers.png)

ECMA 335 II.25.1, çalışma zamanı dosya biçimi yapısını derleme üst bilgiler.

## <a name="processing-the-assemblies"></a>Derlemeleri işleme

Araç veya API'lerden işlem derlemelere yazmak mümkündür. Derleme bilgilerini, çalışma zamanında programlı kararların, derlemeleri yeniden yazma, düzenleyicideki API IntelliSense sağlamak ve belgeleri oluşturuluyor sağlar. <xref:System.Reflection?displayProperty=nameWithType> ve [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) bu amaç için sık kullanılan araçlar için iyi örneklerdir.
