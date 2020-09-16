---
title: 'Nasıl yapılır: .NET Framework ve Windows Çalışma Zamanı akışları arasında dönüştürme (yalnızca Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 037ae0dff80c96d08d8778146b5683454b1f80b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543698"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Nasıl yapılır: .NET Framework ve Windows Çalışma Zamanı akışları arasında dönüştürme (yalnızca Windows)

UWP uygulamaları için .NET Framework, tam .NET Framework bir alt kümesidir. UWP uygulamalarına yönelik güvenlik ve diğer gereksinimler nedeniyle, dosyaları açmak ve okumak için .NET Framework API 'lerin tam kümesini kullanamazsınız. Daha fazla bilgi için bkz. [UWP uygulamalarına yönelik .NET genel bakış](/previous-versions/windows/apps/br230302(v=vs.140)). Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışları işlemek için, veya gibi bir .NET Framework Stream türü arasında dönüştürme yapabilirsiniz <xref:System.IO.MemoryStream> ve, <xref:System.IO.FileStream> veya gibi bir Windows çalışma zamanı akışı <xref:Windows.Storage.Streams.IInputStream> <xref:Windows.Storage.Streams.IOutputStream> <xref:Windows.Storage.Streams.IRandomAccessStream> .

<xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType>Sınıfı, bu dönüştürmeleri kolaylaştıran yöntemler içerir. Ancak, .NET Framework ve Windows Çalışma Zamanı akışları arasındaki temel farklılıklar, aşağıdaki bölümlerde açıklandığı gibi, bu yöntemlerin kullanılmasıyla ilgili sonuçları etkiler:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı .NET Framework akışına dönüştürme
Bir Windows Çalışma Zamanı akışından .NET Framework akışına dönüştürmek için aşağıdaki yöntemlerden birini kullanın <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> :

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> Windows Çalışma Zamanı bir rastgele erişim akışını UWP uygulamaları için .NET 'teki yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType> UWP uygulamaları için Windows Çalışma Zamanı bir çıktı akışını .NET 'teki yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> UWP uygulamaları için Windows Çalışma Zamanı bir giriş akışını .NET 'teki yönetilen bir akışa dönüştürür.

Windows Çalışma Zamanı, yalnızca okumayı, yalnızca yazmayı veya okumayı ve yazmayı destekleyen akış türleri sunar. Bu yetenekler, bir Windows Çalışma Zamanı akışını .NET Framework akışına dönüştürdüğünüzde sürdürülür. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız.

Dönüştürmek istediğiniz Windows Çalışma Zamanı akışının özellikleri ile eşleşen dönüştürme yöntemini kullanmak en iyi uygulamadır. Ancak, <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir ve yazılabilir olduğundan (hem hem de uygular <xref:Windows.Storage.Streams.IOutputStream> <xref:Windows.Storage.Streams.IInputStream> ), dönüştürme yöntemleri özgün akışın yeteneklerini korur. Örneğin, bunu <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> dönüştürmek için kullanmak, <xref:Windows.Storage.Streams.IRandomAccessStream> dönüştürülmüş .NET Framework akışını okunamala sınırlar. Aynı zamanda yazılabilir.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Örnek: Windows Çalışma Zamanı .NET Framework akışa rastgele erişim dönüştürme
Windows Çalışma Zamanı Rastgele erişimli bir akıştan .NET Framework akışına dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> yöntemini kullanın.

Aşağıdaki kod örneği, bir dosya seçmenizi, dosyayı Windows Çalışma Zamanı API 'lerle açmanızı ve ardından bunu bir .NET Framework akışına dönüştürmenizi ister. Akışı okur ve bir metin bloğuna çıkarır. Sonuçları yazmadan önce genellikle akışı .NET Framework API 'Leri ile işleyebilirsiniz.

Bu örneği çalıştırmak için adlı bir metin bloğu ve adında bir düğme içeren bir UWP XAML uygulaması oluşturun `TextBlock1`  `Button1` . Düğme tıklama olayını `button1_Click` örnekte gösterilen yöntemle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Bir .NET Framework Windows Çalışma Zamanı akışına dönüştürme
Bir .NET Framework akışından Windows Çalışma Zamanı akışına dönüştürmek için aşağıdaki yöntemlerden birini kullanın <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> :

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> UWP uygulamaları için .NET içindeki yönetilen bir akışı, Windows Çalışma Zamanı giriş akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> UWP uygulamaları için .NET içindeki yönetilen bir akışı, Windows Çalışma Zamanı bir çıkış akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType> UWP uygulamaları için .NET içindeki yönetilen bir akışı, Windows Çalışma Zamanı okuma veya yazma için kullanabileceği Rastgele erişimli bir akışa dönüştürür.

Bir .NET Framework akışını Windows Çalışma Zamanı akışına dönüştürdüğünüzde, dönüştürülen akışın özellikleri orijinal akışa bağlıdır. Örneğin, özgün akış hem okumayı hem yazmayı destekliyorsa ve <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> akışı dönüştürmek için çağırdığınızda döndürülen tür bir olur `IRandomAccessStream` . `IRandomAccessStream``IInputStream`, ve `IOutputStream` ' ı uygular ve okumayı ve yazmayı destekler.

.NET Framework akışları, dönüştürme işleminden sonra bile kopyalamayı desteklemez. Bir .NET Framework akışını Windows Çalışma Zamanı bir akışa dönüştürürseniz <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> veya çağırmak ya da <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A> <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> doğrudan çağırdıysanız, <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> bir özel durum oluşur.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Örnek: .NET Framework Windows Çalışma Zamanı Rastgele erişimli akışa Dönüştür

.NET Framework akışından Windows Çalışma Zamanı Rastgele erişimli akışa dönüştürmek için, <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> Aşağıdaki örnekte gösterildiği gibi yöntemini kullanın:

> [!IMPORTANT]
> Kullanmakta olduğunuz .NET Framework akışının aramayı desteklediğinden emin olun veya bunu yapan bir akışa kopyalayın. <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType>Bunu anlamak için özelliğini kullanabilirsiniz.

Bu örneği çalıştırmak için, .NET Framework 4.5.1 hedefleyen ve adlı bir metin bloğu ve adlı bir düğme içeren bir UWP XAML uygulaması oluşturun `TextBlock2` `Button2` . Düğme tıklama olayını `button2_Click` örnekte gösterilen yöntemle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: dosya okuma ve yazma (Windows)](/previous-versions/windows/apps/hh464978(v=win.10))  
- [Windows Mağazası uygulamalarına yönelik .NET genel bakış](/previous-versions/windows/apps/br230302(v=vs.140))  
- [Windows Mağazası uygulamaları için .NET API 'Leri](/previous-versions/br230232(v=vs.120))
