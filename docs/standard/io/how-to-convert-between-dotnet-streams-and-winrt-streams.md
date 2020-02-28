---
title: 'Nasıl yapılır: .NET Framework ve Windows Çalışma Zamanı akışları arasında dönüştürme (yalnızca Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159474"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Nasıl yapılır: .NET Framework ve Windows Çalışma Zamanı akışları arasında dönüştürme (yalnızca Windows)

UWP uygulamaları için .NET Framework, tam .NET Framework bir alt kümesidir. UWP uygulamalarına yönelik güvenlik ve diğer gereksinimler nedeniyle, dosyaları açmak ve okumak için .NET Framework API 'lerin tam kümesini kullanamazsınız. Daha fazla bilgi için bkz. [UWP uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışları işlemek için, <xref:System.IO.MemoryStream> veya <xref:System.IO.FileStream>gibi bir .NET Framework Stream türü arasında ve <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>veya <xref:Windows.Storage.Streams.IRandomAccessStream>gibi bir Windows Çalışma Zamanı akışı arasında dönüştürme yapabilirsiniz.

<xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> sınıfı, bu dönüştürmeleri kolaylaştıran yöntemler içerir. Ancak, .NET Framework ve Windows Çalışma Zamanı akışları arasındaki temel farklılıklar, aşağıdaki bölümlerde açıklandığı gibi, bu yöntemlerin kullanılmasıyla ilgili sonuçları etkiler:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı .NET Framework akışına dönüştürme
Bir Windows Çalışma Zamanı akışından .NET Framework akışına dönüştürmek için aşağıdaki <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> yöntemlerinden birini kullanın:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>, Windows Çalışma Zamanı bir rastgele erişim akışını UWP uygulamaları için .NET 'teki yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType>, Windows Çalışma Zamanı bir çıktı akışını UWP uygulamaları için .NET 'teki yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType>, Windows Çalışma Zamanı bir giriş akışını UWP uygulamaları için .NET 'teki yönetilen bir akışa dönüştürür.

Windows Çalışma Zamanı, yalnızca okumayı, yalnızca yazmayı veya okumayı ve yazmayı destekleyen akış türleri sunar. Bu yetenekler, bir Windows Çalışma Zamanı akışını .NET Framework akışına dönüştürdüğünüzde sürdürülür. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız.

Dönüştürmek istediğiniz Windows Çalışma Zamanı akışının özellikleri ile eşleşen dönüştürme yöntemini kullanmak en iyi uygulamadır. Ancak, <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir ve yazılabilir olduğundan (hem <xref:Windows.Storage.Streams.IOutputStream> hem de <xref:Windows.Storage.Streams.IInputStream>uygular), dönüştürme yöntemleri özgün akışın yeteneklerini korur. Örneğin, bir <xref:Windows.Storage.Streams.IRandomAccessStream> dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> kullanmak, dönüştürülen .NET Framework akışını okunabilir olarak sınırlandırmaz. Aynı zamanda yazılabilir.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Örnek: Windows Çalışma Zamanı .NET Framework akışa rastgele erişim dönüştürme
Windows Çalışma Zamanı Rastgele erişimli bir akıştan .NET Framework akışına dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> yöntemini kullanın.

Aşağıdaki kod örneği, bir dosya seçmenizi, dosyayı Windows Çalışma Zamanı API 'lerle açmanızı ve ardından bunu bir .NET Framework akışına dönüştürmenizi ister. Akışı okur ve bir metin bloğuna çıkarır. Sonuçları yazmadan önce genellikle akışı .NET Framework API 'Leri ile işleyebilirsiniz.

Bu örneği çalıştırmak için, `TextBlock1` adlı bir metin bloğunu ve `Button1`adlı bir düğmeyi içeren UWP XAML uygulaması oluşturun. Düğme tıklama olayını örnekte gösterilen `button1_Click` yöntemiyle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Bir .NET Framework Windows Çalışma Zamanı akışına dönüştürme
Bir .NET Framework akışından Windows Çalışma Zamanı akışına dönüştürmek için aşağıdaki <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> yöntemlerinden birini kullanın:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType>, UWP uygulamaları için .NET 'teki yönetilen bir akışı Windows Çalışma Zamanı bir giriş akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> UWP uygulamaları için .NET 'teki yönetilen bir akışı Windows Çalışma Zamanı bir çıkış akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType>, UWP uygulamaları için .NET içindeki yönetilen bir akışı, Windows Çalışma Zamanı okuma veya yazma için kullanabileceği Rastgele erişimli bir akışa dönüştürür.

Bir .NET Framework akışını Windows Çalışma Zamanı akışına dönüştürdüğünüzde, dönüştürülen akışın özellikleri orijinal akışa bağlıdır. Örneğin, özgün akış hem okumayı hem yazmayı destekliyorsa ve akışı dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> çağırırsanız, döndürülen tür bir `IRandomAccessStream`. `IRandomAccessStream` `IInputStream` ve `IOutputStream`uygular ve okumayı ve yazmayı destekler.

.NET Framework akışları, dönüştürme işleminden sonra bile kopyalamayı desteklemez. Bir .NET Framework akışı Windows Çalışma Zamanı bir akışa dönüştürürseniz ve <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>çağıran <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> ya da <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>ve doğrudan çağrı yaparsanız bir özel durum oluşur.<xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Örnek: .NET Framework Windows Çalışma Zamanı Rastgele erişimli akışa Dönüştür

.NET Framework akışından Windows Çalışma Zamanı Rastgele erişimli akışa dönüştürmek için aşağıdaki örnekte gösterildiği gibi <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> metodunu kullanın:

> [!IMPORTANT]
> Kullanmakta olduğunuz .NET Framework akışının aramayı desteklediğinden emin olun veya bunu yapan bir akışa kopyalayın. Bunu öğrenmek için <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.

Bu örneği çalıştırmak için, .NET Framework 4.5.1 hedefleyen ve `TextBlock2` adlı bir metin bloğu ve `Button2`adlı bir düğme içeren bir UWP XAML uygulaması oluşturun. Düğme tıklama olayını örnekte gösterilen `button2_Click` yöntemiyle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: dosya okuma ve yazma (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Windows Mağazası uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [Windows Mağazası uygulamaları için .NET API 'Leri](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
