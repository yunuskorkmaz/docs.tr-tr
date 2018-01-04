---
title: ".NET derleme dosyası biçimi"
description: "Tanımlamak ve .NET uygulamalarını ve kitaplıklarını içermesi için kullanılan .NET derleme dosya biçimine hakkında bilgi edinin."
keywords: .NET, .NET core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 94f102c85ffdda5345a3ef3f0a8485b18b0b6893
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-assembly-file-format"></a>.NET derleme dosyası biçimi

.NET tam olarak tanımlamak ve .NET programları içeren için kullanılan bir ikili dosya biçimi - "derlemesi" - tanımlar. Derlemeler, tüm bağımlı kitaplıkları yanı sıra program kendileri için kullanılır. Bir .NET program hiçbir diğer gerekli yapılarına uygun .NET uygulaması ötesinde ile daha fazla derlemeleri biri olarak çalıştırılabilir. İşletim sistemi API'leri dahil olmak üzere yerel bağımlılıklar ayrı bir sorun olduğundan ve bazen bu biçimle (örneğin, WinRT) açıklanan rağmen .NET derleme biçimi içinde yer almayan.

> Her CLI bileşen bildirimler, uygulamalar ve bu bileşen için belirli başvuruları için meta verileri taşır. Bu nedenle, bileşen özgü meta veriler bileşen meta adlandırılır ve sonuçta elde edilen bileşen – ECMA 335 I.9.1, bileşenleri ve derlemeler kendiliğinden açıklayıcı olması söylenir.

Biçimi tam olarak belirtilen ve ECMA 335 standartlaştırılmıştır. Tüm .NET derleyicileri ve çalışma zamanları şu biçimi kullanın. Belgelenmiş ve seyrek güncelleştirilmiş bir ikili biçimi varlığını (tartışmaya açık bir şekilde bir gereksinim) önemli bir avantajı birlikte çalışabilirliği için bırakıldı. Biçim son genel türler ve işlemci mimarisi uyum sağlayacak şekilde (.NET 2.0) 2005'te substantive şekilde güncelleştirildi.

CPU ve işletim sistemi belirsiz biçimindedir. Birçok yongaları ve CPU'yu hedef .NET uygulamalarında bir parçası olarak kullanılmış. Biçim Windows miras sahipken, herhangi bir işletim sisteminde implementable. Buna ait tartışmaya açık bir şekilde en önemli işletim sistemi birlikte çalışabilirlik için çoğu değerler little endian biçiminde depolanır seçimdir. Belirli bir benzeşim makine işaretçi boyutuna (örneğin, 32-bit, 64-bit) sahip değil.

.NET derleme de verilen programı veya kitaplık yapısı hakkında çok açıklayıcı biçimidir. Bir derlemeyi iç bileşenlerinin özellikle açıklanmaktadır: derleme başvurularını ve tanımlanan türleri ve kendi iç yapısı. Araçları veya API'ler, okuma ve bu bilgileri görüntülemek veya programlama kararlar almak için işlem.

## <a name="format"></a>Biçimi

.NET ikili biçimi Windows tabanlı [PE dosya](http://en.wikipedia.org/wiki/Portable_Executable) biçimi. Aslında, .NET sınıf kitaplıkları uyumluluğunu Windows PEs olan ve üzerinde ilk bakışta Windows dinamik bağlantı kitaplıklarını (DLL'ler) veya uygulama yürütülebilir dosyalar (exe) olarak görünür. Bu, burada bunlar geçici yerel yürütülebilir ikili dosyaları ve bazı (örneğin, işletim sistemi yükleme, PE Araçları) aynı işleme almak Windows çok kullanışlı bir özellik değildir.

![Derleme üstbilgileri](./media/assembly-format/assembly-headers.png)

ECMA 335 II.25.1, çalışma zamanı dosya biçimi yapısını derleme üstbilgileri.

## <a name="processing-the-assemblies"></a>Derlemeleri işleme

İşlem derlemeler için yazma araçları veya API'ler mümkündür. Derleme bilgilerini çalışma zamanında programlı kararları, derlemeleri yeniden yazma, API IntelliSense bir düzenleyicide sağlama ve belgeleri oluşturma sağlar. <xref:System.Reflection?displayProperty=nameWithType>ve [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) bu amaç için sık kullanılan araçların iyi örnekleri verilmiştir.
