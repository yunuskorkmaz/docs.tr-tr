---
title: .NET Yerel ile Uygulama Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128382"
---
# <a name="compiling-apps-with-net-native"></a>.NET Yerel ile Uygulama Derleme

.NET Native, Visual Studio 2015 ve sonraki sürümlerinde bulunan Windows uygulamaları oluşturmak ve dağıtmak için ön derleme teknolojisidir. Yönetilen kodda (C# veya Visual Basic) yazılmış uygulamaların yayın sürümünü otomatik olarak derler ve .NET Framework ve Windows 10 ' a yerel koda hedefleyin.

Genellikle, .NET Framework hedefleyen uygulamalar ara dil (IL) ile derlenir. Çalışma zamanında, tam zamanında (JıT) derleyici, Il 'yi yerel koda dönüştürür. Buna karşılık, Windows uygulamalarını doğrudan yerel koda derler .NET Native. Geliştiriciler için şu anlama gelir:

- Uygulamalarınızın yerel kodun performansı vardır. Genellikle, ilk olarak Il 'de derlenen ve sonra JıT derleyicisi tarafından yerel koda derlenen kodların üst işlemi olur.

- C# veya Visual Basic programla çalışmaya devam edebilirsiniz.

- Sınıf kitaplığı, otomatik bellek yönetimi ve çöp toplama ve özel durum işleme dahil olmak üzere .NET Framework tarafından belirtilen kaynaklardan faydalanmaya devam edebilirsiniz.

Uygulamalarınızın kullanıcıları için .NET Native şu avantajları sunar:

- Uygulama ve senaryoların çoğunluğu için daha hızlı yürütme süreleri.

- Uygulama ve senaryoların çoğunluğu için daha hızlı başlangıç süreleri.

- Düşük dağıtım ve güncelleştirme maliyetleri.

- En iyileştirilmiş uygulama bellek kullanımı.

> [!IMPORTANT]
> Uygulamalar ve senaryoların büyük çoğunluğu için .NET Native, Il 'ye veya NGEN görüntüsüne derlenen bir uygulamayla karşılaştırıldığında önemli ölçüde daha hızlı başlangıç süreleri ve üstün performans sunar. Ancak, sonuçlarınız farklılık gösterebilir. Uygulamanızın .NET Native performans geliştirmelerinden benefited sahip olduğundan emin olmak için, performansını uygulamanızın non-.NET Native sürümüyle karşılaştırmalısınız. Daha fazla bilgi için bkz. [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Ancak .NET Native yerel koda bir derlemeden daha fazlasını içerir. .NET Framework uygulamalarının oluşturulması ve yürütülmesi şeklini dönüştürür. Özellikle:

- Ön derleme sırasında .NET Framework gerekli bölümleri uygulamanıza statik olarak bağlanır. Bu, uygulamanın .NET Framework uygulama yerel kitaplıklarıyla çalışmasına ve derleyicinin küresel bir şekilde performans sağlamak için genel analizler gerçekleştirmesini sağlar. Sonuç olarak, uygulamalar .NET Framework güncelleştirmelerden sonra bile sürekli olarak daha hızlı başlatılır.

- .NET Native çalışma zamanı statik ön derleme için iyileştirilmiştir ve durumların büyük çoğunluğunda üstün performans sağlar. Aynı zamanda, geliştiricilerin daha üretken bulduğu temel yansıma özelliklerini korur.

- .NET Native, statik ön derleme senaryolarında en iyi duruma getirilmiş C++ derleyicisi ile aynı arka ucu kullanır.

.NET Native, bu tabloda gösterildiği gibi, aynı veya benzer araçlarla C++ ile aynı veya benzer araçları kullandığından, C++ ' ın performans avantajlarını yönetilen kod geliştiricilerine getirebiliyor.

||.NET Yerel|C++|
|-|----------------------------------------------------------------|-----------|
|Kitaplıklar|.NET Framework + Windows Çalışma Zamanı|Win32 + Windows Çalışma Zamanı|
|Derleyici|UTC iyileştirmeli derleyici|UTC iyileştirmeli derleyici|
|Dağıtılan|Çalıştırılmaya hazırlama ikilileri|Çalıştırılmaya hazırlama ikilileri (ASM)|
|Çalışma Zamanı|MRT. dll (minimum CLR Runtime)|CRT. dll (C çalışma zamanı)|

Windows 10 için Windows uygulamaları için, uygulama paketlerinde (. appx dosyaları) .NET Native kod derleme ikililerini Windows Mağazası 'na yüklersiniz.

## <a name="in-this-section"></a>Bu Bölümde

.NET Native kod derlemesi ile uygulama geliştirme hakkında daha fazla bilgi için şu konulara bakın:

- [.NET Native kod derleme ile çalışmaya başlama: geliştirici deneyimi Kılavuzu](getting-started-with-net-native.md)

- [.NET Native ve derleme:](net-native-and-compilation.md) .NET Native projenizi yerel koda nasıl derler.

- [Yansıma ve .NET Yerel](reflection-and-net-native.md)

  - [Yansıma kullanan API'ler](apis-that-rely-on-reflection.md)

  - [Yansıma API'si Başvurusu](net-native-reflection-api-reference.md)

  - [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)

- [Serileştirme ve Meta Veriler](serialization-and-metadata.md)

- [Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma](migrating-your-windows-store-app-to-net-native.md)

- [.NET Yerel Genel Sorun Giderme](net-native-general-troubleshooting.md)
