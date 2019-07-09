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
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660897"
---
# <a name="compiling-apps-with-net-native"></a>.NET Yerel ile Uygulama Derleme

.NET native, Visual Studio 2015 ve sonraki sürümlerine dahildir oluşturmak ve Windows uygulamalarını dağıtmak için bir ön derleme teknolojisidir. Yönetilen kodda yazılmış uygulamalar yayım sürümünü otomatik olarak derler (C# veya Visual Basic) ve hedef .NET Framework ve Windows 10 için yerel kod.

Genellikle, .NET Framework'ü hedefleyen uygulamaları Ara dil (IL) derlenir. Çalışma zamanında, just-ın-time (JIT) derleyici yerel kod için IL çevirir. Buna karşılık, .NET yerel Windows uygulamaları doğrudan yerel kod için derler. Geliştiriciler için bu anlamına gelir:

- Uygulamalarınızı yerel kod performansını özellik. Genellikle, performans için IL önce derlenmiş ve sonra JIT derleyicisi tarafından yerel kod olarak derlenen kod için üstün olacaktır.

- İçinde program devam edebilirsiniz C# veya Visual Basic.

- Kendi sınıf kitaplığı, otomatik bellek yönetimi ve atık toplama ve özel durum işleme dahil olan .NET Framework tarafından sağlanan kaynaklar yararlanmak devam edebilirsiniz.

Uygulamalarınızın kullanıcılar için .NET Native aşağıdaki avantajları sunar:

- Çoğu uygulama ve senaryoları için daha hızlı yürütme süreleri.

- Çoğu uygulama ve senaryoları için daha hızlı başlangıç süreleri.

- Dağıtım ve güncelleştirme maliyetleri düşük.

- Uygulamanın bellek kullanımı İyileştirildi.

> [!IMPORTANT]
> Uygulamalar ve senaryoları büyük çoğunluğu için .NET Native önemli ölçüde daha hızlı başlangıç süreleri ve IL veya NGEN görüntü için derlenmiş uygulama karşılaştırıldığında daha üstün performans sunar. Ancak, sonuçlar farklılık gösterebilir. Uygulamanızı .NET Native'nın performans iyileştirmeleriyle benefited olmak için performansını, uygulamanızın .NET Native sürümü ile karşılaştırmanız gerekir. Daha fazla bilgi için [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Ancak, .NET yerel derleme yerel kod için birden fazla içerir. Bu, .NET Framework uygulamaları yerleşik ve yürütülen şekilde dönüştürür. Özellikle:

- Esnasında, gerekli bölümleri .NET Framework'ün uygulamanıza statik olarak bağlanır. Bu uygulamanın .NET Framework ve derleyici genel analiz gerçekleştirmek için performans WINS sunmak için uygulama yerel kitaplıkları ile çalışmasını sağlar. Sonuç olarak, uygulamaları bile .NET Framework güncelleştirmeleri sonrasında tutarlı bir şekilde daha hızlı başlatma.

- .NET yerel çalışma zamanı statik ön derleme için en iyi duruma getirilmiş ve çalışmaları büyük çoğunluğu üstün performans sunar. Aynı anda geliştiricileri kadar üretken Bul temel yansıma özelliklerini korur.

- .NET native kullandığı aynı arka uç olarak C++ statik ön derleme senaryolar için en iyi duruma getirilmiş derleyici.

.NET native performans avantajlarını ürünümüze C++ yönetilen kod geliştiricilerin olarak aynı veya benzer araçları kullandığından C++ bu tabloda gösterildiği gibi başlık altında.

||.NET Yerel|C++|
|-|----------------------------------------------------------------|-----------|
|Kitaplıklar|.NET Framework ve Windows çalışma zamanı|Win32 + Windows çalışma zamanı|
|Derleyici|İyileştirici derleyiciyi UTC|İyileştirici derleyiciyi UTC|
|dağıtılan|Çalıştırılmaya hazır ikili dosyaları|Çalıştırılmaya hazır ikili dosyaları (ASM)|
|Çalışma zamanı|MRT.dll (Minimal CLR Runtime)|CRT.dll (C Runtime)|

Windows 10 için Windows uygulamaları için .NET yerel kodu derleme ikili dosyaları uygulama paketleri (.appx dosyaları) için Windows Store yükleyin.

## <a name="in-this-section"></a>Bu Bölümde

.NET yerel kodu derleme ile uygulamaları geliştirme hakkında daha fazla bilgi için şu konulara bakın:

- [.NET yerel kodu derlemesi ile çalışmaya başlama: Geliştirici deneyimi Kılavuzu](../../../docs/framework/net-native/getting-started-with-net-native.md)

- [.NET native ve derleme:](../../../docs/framework/net-native/net-native-and-compilation.md) Nasıl .NET Native yerel kod projenize derler.

- [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [Yansıma Kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [Yansıma API'si Başvurusu](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [Serileştirme ve Meta Veriler](../../../docs/framework/net-native/serialization-and-metadata.md)

- [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [.NET Native Genel Sorun Giderme](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
