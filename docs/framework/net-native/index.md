---
title: .NET Yerel ile Uygulama Derleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dec4d465b53f939f8fa711950ba6a000bd304e13
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="compiling-apps-with-net-native"></a>.NET Yerel ile Uygulama Derleme
[!INCLUDE[net_native](../../../includes/net-native-md.md)]Visual Studio 2015 ve sonraki sürümleri ile birlikte oluşturmak ve Windows uygulamalarını dağıtmak için bir ön derleme teknolojisidir. Ayrıca yönetilen kod (C# veya Visual Basic) ve bu hedef .NET Framework ve Windows 10 yerel koda yazılan uygulamaları sürümünü otomatik olarak derler.  
  
 Genellikle, .NET Framework hedefleyen uygulamalar Ara dile (IL) derlenir. Çalışma zamanında tam zamanında (JIT) Derleyici IL yerel koda çevirir. Buna karşılık, [!INCLUDE[net_native](../../../includes/net-native-md.md)] Windows uygulamaları doğrudan yerel kod derler. Geliştiriciler için bu anlamına gelir:  
  
-   Yerel kod performansını uygulamalarınızı özelliği. Genellikle, performans ilk IL için derlenmiş ve ardından JIT Derleyici tarafından yerel koda derlenmiş kod üstün olacaktır. 
  
-   C# veya Visual Basic programı devam edebilirsiniz.  
  
-   Sınıf kitaplığı, otomatik bellek yönetimi ve çöp toplama ve özel durum işleme dahil olan .NET Framework tarafından sağlanan kaynaklar yararlanmak devam edebilirsiniz.  
  
 Uygulamalarınızın, kullanıcılar için [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdaki avantajları sunar:  
  
-   Uygulamaları ve senaryoları çoğunluğu için daha hızlı yürütme süresi.
  
-   Uygulamaları ve senaryoları çoğunluğu daha hızlı başlatma sürelerinin. 
  
-   Düşük dağıtım ve güncelleştirme maliyetleri.  
  
-   En iyi duruma getirilmiş uygulama bellek kullanımı.  

> [!IMPORTANT]
> Uygulamaları ve senaryoları büyük çoğunluğu için .NET yerel önemli ölçüde daha hızlı başlangıç süreleri ve IL veya NGEN görüntü için derlenmiş bir uygulama karşılaştırıldığında üstün performans sunar. Ancak, sonuçlarınızı farklılık gösterebilir. Uygulamanız .NET yerel olarak performans iyileştirmeleriyle benefited olmak için uygulamanızı .NET yerel sürümü ile kendi performansını karşılaştırmanız gerekir. Daha fazla bilgi için bkz: [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Ancak [!INCLUDE[net_native](../../../includes/net-native-md.md)] birden çok derleme yerel koda içerir. .NET Framework uygulamalarını yerleşik ve yürütülen şekilde dönüştürür. Özellikle:  
  
-   Ön derlemesi esnasında, .NET Framework'ün gerekli bölümleri uygulamanıza statik olarak bağlanır. Bu, .NET Framework ve derleyici global analizi yapmak için performans WINS teslim etmek için uygulama yerel kitaplıklarıyla çalıştırmak için uygulamayı sağlar. Sonuç olarak, .NET Framework bile güncelleştirildikten sonra uygulamaları tutarlı bir şekilde daha hızlı başlatın.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı statik ön derlemesi için en iyi duruma getirilmiş ve çoğunluğu durumlarda üstün performans sunar. Aynı anda geliştiricilere kadar üretken Bul çekirdek yansıma özellikleri korur.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]kullandığı aynı geri statik ön derleme senaryoları için en iyi duruma getirilmiş C++ derleyicisi olarak sonlandırın.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]başlık altında C++ aynı veya benzer araçları kullandığından C++ performans yararlarını yönetilen kod geliştiricilerin bu tabloda gösterildiği gibi Getir yapabiliyor.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Kitaplıklar|.NET Framework + Windows çalışma zamanı|Win32 + Windows çalışma zamanı|  
|Derleyici|UTC en iyi duruma getirme derleyici|UTC en iyi duruma getirme derleyici|  
|Dağıtılan|Hazır Çalıştır ikili dosyalar|Hazır Çalıştır ikili dosyaları (ASM)|  
|Çalışma zamanı|MRT.dll (en az CLR çalışma zamanı)|CRT.dll (C çalışma zamanı)|  
  
 Windows 10 için Windows uygulamaları için Windows Mağazası'na .NET yerel kodu derleme ikili dosyalarda uygulama paketleri (.appx dosyaları) yükleyin.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 .NET yerel kodu derleme ile uygulamaları geliştirme hakkında daha fazla bilgi için şu konulara bakın:  
  
-   [.NET yerel kodu derleme ile Başlarken: geliştirici deneyimi gözden geçirme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET yerel ve derleme:](../../../docs/framework/net-native/net-native-and-compilation.md) yerel kod projenize .NET nasıl yerel derler.  
  
-   [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [Yansıma Kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [Yansıma API'si Başvurusu](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [Serileştirme ve Meta Veriler](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [.NET Native Genel Sorun Giderme](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET yerel ile ilgili SSS](http://msdn.microsoft.com/vstudio/dn642499.aspx)
