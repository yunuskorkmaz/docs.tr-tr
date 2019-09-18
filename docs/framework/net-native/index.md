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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5993cfdb0f50d8e474a4f18280d181d9ec2fdfa4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049662"
---
# <a name="compiling-apps-with-net-native"></a>.NET Yerel ile Uygulama Derleme

.NET Native, Visual Studio 2015 ve sonraki sürümlerinde bulunan Windows uygulamaları oluşturmak ve dağıtmak için ön derleme teknolojisidir. Yönetilen kodda (C# veya Visual Basic) yazılmış olan ve .NET Framework ve Windows 10 ' un yerel koda hedef alan uygulamaların yayın sürümünü otomatik olarak derler.

Genellikle, .NET Framework hedefleyen uygulamalar ara dil (IL) ile derlenir. Çalışma zamanında, tam zamanında (JıT) derleyici, Il 'yi yerel koda dönüştürür. Buna karşılık, Windows uygulamalarını doğrudan yerel koda derler .NET Native. Geliştiriciler için şu anlama gelir:

- Uygulamalarınızın yerel kodun performansı vardır. Genellikle, ilk olarak Il 'de derlenen ve sonra JıT derleyicisi tarafından yerel koda derlenen kodların üst işlemi olur.

- C# Veya Visual Basic programda çalışmaya devam edebilirsiniz.

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

- .NET Native, C++ derleyici ile aynı arka ucu kullanarak statik ön derleme senaryolarında en iyi duruma getirilmiştir.

.NET Native, bu tabloda gösterildiği gibi, aynı veya C++ benzer araçları C++ kullandığından, yönetilen kod geliştiricilerine ait performans avantajlarını getirebiliyor.

||.NET Yerel|C++|
|-|----------------------------------------------------------------|-----------|
|Kitaplıklar|.NET Framework + Windows Çalışma Zamanı|Win32 + Windows Çalışma Zamanı|
|Derleyici|UTC iyileştirmeli derleyici|UTC iyileştirmeli derleyici|
|Dağıtılan|Çalıştırılmaya hazırlama ikilileri|Çalıştırılmaya hazırlama ikilileri (ASM)|
|Çalışma zamanı|MRT. dll (minimum CLR Runtime)|CRT. dll (C çalışma zamanı)|

Windows 10 için Windows uygulamaları için, uygulama paketlerinde (. appx dosyaları) .NET Native kod derleme ikililerini Windows Mağazası 'na yüklersiniz.

## <a name="in-this-section"></a>Bu Bölümde

.NET Native kod derlemesi ile uygulama geliştirme hakkında daha fazla bilgi için şu konulara bakın:

- [.NET Native kodu derleme ile çalışmaya başlama: Geliştirici deneyimi Kılavuzu](getting-started-with-net-native.md)

- [.NET Native ve derleme:](net-native-and-compilation.md) .NET Native projenizi yerel koda nasıl derler.

- [Yansıma ve .NET Native](reflection-and-net-native.md)

  - [Yansıma Kullanan API'ler](apis-that-rely-on-reflection.md)

  - [Yansıma API'si Başvurusu](net-native-reflection-api-reference.md)

  - [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)

- [Serileştirme ve Meta Veriler](serialization-and-metadata.md)

- [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](migrating-your-windows-store-app-to-net-native.md)

- [.NET Native Genel Sorun Giderme](net-native-general-troubleshooting.md)
