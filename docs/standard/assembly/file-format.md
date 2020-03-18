---
title: .NET derlemesi dosya biçimi
description: .NET uygulamalarını ve kitaplıklarını tanımlamak ve içeren .NET derleme dosya biçimi hakkında bilgi edinin.
author: richlander
ms.date: 08/20/2019
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 4cf6522d66d7a1efccde45078768a773db6e6cb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711590"
---
# <a name="net-assembly-file-format"></a>.NET derlemesi dosya biçimi

.NET, .NET programlarını tam olarak tanımlamak ve içermek için kullanılan bir ikili dosya biçimi, *derleme*tanımlar. Derlemeler programların kendileri ve bağımlı kitaplıklar için kullanılır. Bir .NET programı, uygun .NET uygulamasının ötesinde, gerekli başka bir yapı olmadan bir veya daha fazla derleme olarak yürütülebilir. İşletim sistemi API'leri de dahil olmak üzere yerel bağımlılıklar ayrı bir sorundur ve .NET derleme biçimi içinde yer almamakla birlikte bazen bu biçimle (örneğin, WinRT) açıklanırlar.

> Her CLI bileşeni, bu bileşene özgü bildirimler, uygulamalar ve başvurular için meta verileri taşır. Bu nedenle, bileşene özgü meta veriler bileşen meta verileri olarak adlandırılır ve elde edilen bileşenin ECMA 335 I.9.1 Bileşenleri ve derlemelerinden kendi kendini tanımladığı söylenir.

Format tamamen belirtilmiştir ve [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm)olarak standartlaştırılmıştır. Tüm .NET derleyicileri ve çalışma saatleri bu biçimi kullanır. Belgelenmiş ve seyrek güncelleştirilen ikili biçimin varlığı birlikte çalışabilirlik için önemli bir avantaj (muhtemelen bir gereklilik) olmuştur. Biçim en son 2005 yılında (.NET 2.0) genel jenerik ve işlemci mimarisini barındıracak şekilde önemli bir şekilde güncelleştirildi.

Biçimi CPU ve OS-agnostik. Birçok fiş ve CPU'ları hedefleyen .NET uygulamalarının bir parçası olarak kullanılmıştır. Biçimin kendisi Windows mirasına sahip olsa da, herhangi bir işletim sisteminde uygulanabilir. İşletim sistemi birlikte çalışabilirliği için tartışmasız en önemli seçenek, çoğu değerin az en son biçimde depolanmış olmasıdır. Makine işaretçisi boyutuna belirli bir yakınlığı yoktur (örneğin, 32-bit, 64-bit).

.NET derleme biçimi de belirli bir programın veya kitaplığın yapısı hakkında çok açıklayıcıdır. Bir derlemenin iç bileşenlerini, özellikle montaj başvurularını ve tanımlanan türleri ve bunların iç yapısını açıklar. Araçlar veya API'ler bu bilgileri görüntülemek veya programlı kararlar almak için okuyabilir ve işleyebilir.

## <a name="format"></a>Biçimlendir

.NET ikili biçimi Windows [PE dosya](https://en.wikipedia.org/wiki/Portable_Executable) biçimini temel alınr. Aslında, .NET sınıf kitaplıkları uyumlu Windows SÜRÜ'leridir ve ilk bakışta Windows dinamik bağlantı kitaplıkları (DL'ler) veya uygulama yürütülebilirleri (EX'ler) olarak görünür. Bu, windows üzerinde çok yararlı bir özelliktir, burada yerel yürütülebilir ikililer kılığına ve bazı aynı tedavi (örneğin, işletim sistemi yükü, PE araçları) almak.

![Montaj üstbilgi](../media/assembly-format/assembly-headers.png)

ECMA 335 II.25.1'den Derleme Başlıkları, çalışma zamanı dosya biçiminin yapısı.

## <a name="process-the-assemblies"></a>Montajları işleme

Derlemeleri işlemek için araçlar veya API'ler yazmak mümkündür. Derleme bilgileri, çalışma zamanında programlı kararlar almanızı, derlemeleri yeniden yazmanızı, bir düzenleyicide API IntelliSense sağlamanızı ve belgeler oluşturmanızı sağlar. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType>ve [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) sık sık bu amaç için kullanılan araçların iyi örneklerdir.
