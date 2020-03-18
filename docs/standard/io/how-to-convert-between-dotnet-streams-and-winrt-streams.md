---
title: 'Nasıl yapılır: .NET Framework ve Windows Runtime akışları arasında dönüştürme (yalnızca Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159474"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Nasıl yapılır: .NET Framework ve Windows Runtime akışları arasında dönüştürme (yalnızca Windows)

UWP uygulamaları için .NET Framework, tam .NET Framework'ün bir alt kümesidir. Güvenlik ve UWP uygulamaları için diğer gereksinimler nedeniyle, dosyaları açmak ve okumak için .NET Framework API'lerinin tam kümesini kullanamazsınız. Daha fazla bilgi [için UWP uygulamalarına genel bakış için .NET'e](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))bakın. Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışları işlemek için, .NET Framework akışı türü <xref:System.IO.MemoryStream> veya <xref:System.IO.FileStream>,, ve <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, veya <xref:Windows.Storage.Streams.IRandomAccessStream>.

Sınıf, <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> bu dönüşümleri kolaylaştıran yöntemler içerir. Ancak, .NET Framework ve Windows Runtime akışları arasındaki temel farklar, aşağıdaki bölümlerde açıklandığı gibi bu yöntemleri kullanmanın sonuçlarını etkiler:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Windows Runtime'dan .NET Framework akışına dönüştürme
Windows Runtime akışından bir .NET Framework akışına dönüştürmek <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> için aşağıdaki yöntemlerden birini kullanın:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>Windows Runtime'daki rasgele erişim akışını UWP uygulamaları için .NET'te yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType>Windows Runtime'daki bir çıktı akışını UWP uygulamaları için .NET'te yönetilen bir akışa dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType>Windows Runtime'daki bir giriş akışını UWP uygulamaları için .NET'te yönetilen bir akışa dönüştürür.

Windows Runtime yalnızca okumayı, yalnızca yazmayı veya okuma ve yazmayı destekleyen akış türleri sunar. Bu özellikler, bir Windows Runtime akışını bir .NET Framework akışına dönüştürdüğünüzde korunur. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız.

Dönüştürmek istediğiniz Windows Runtime akışının özellikleriyle eşleşen dönüşüm yöntemini kullanmak en iyi yöntemdir. Ancak, <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir ve yazılabilir olduğundan (hem <xref:Windows.Storage.Streams.IOutputStream> <xref:Windows.Storage.Streams.IInputStream>de uygular), dönüştürme yöntemleri özgün akışın yeteneklerini korur. Örneğin, bir <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> dönüştürme <xref:Windows.Storage.Streams.IRandomAccessStream> yi dönüştürmek için kullanmak dönüştürülen .NET Framework akışını okunabilir olmakla sınırlamaz. Aynı zamanda yazılabilir.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Örnek: Windows Runtime rasgele erişimini .NET Framework akışına dönüştürme
Windows Runtime rasgele erişim akışından bir .NET Framework akışına dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> yöntemi kullanın.

Aşağıdaki kod örneği, bir dosya seçmeni ister, Windows Runtime API'leri ile açar ve sonra bir .NET Framework akışına dönüştürür. Akışı okur ve bir metin bloğuna çıkar. Genellikle sonuçları çıkarmadan önce .NET Framework API'leri ile akışı manipüle e-son verirsiniz.

Bu örneği çalıştırmak için, adlı bir metin bloğu ve `TextBlock1` bir düğme `Button1`adlı içeren bir UWP XAML uygulaması oluşturun. Düğme tıklatma olayını `button1_Click` örnekte gösterilen yöntemle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>.NET Framework'den Windows Runtime akışına dönüştürme
.NET Framework akışından Windows Runtime akışına dönüştürmek için <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> aşağıdaki yöntemlerden birini kullanın:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType>UWP uygulamaları için .NET'te yönetilen bir akışı Windows Runtime'daki bir giriş akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType>UWP uygulamaları için .NET'te yönetilen bir akışı Windows Runtime'daki bir çıktı akışına dönüştürür.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType>UWP uygulamaları için .NET'teki yönetilen akışı, Windows Runtime'ın okuma veya yazma için kullanabileceği rasgele erişim akışına dönüştürür.

Bir .NET Framework akışını Windows Runtime akışına dönüştürdüğünüzde, dönüştürülen akışın özellikleri özgün akışa bağlıdır. Örneğin, özgün akış hem okuma hem de yazmayı <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> destekliyorsa ve akışı dönüştürmek `IRandomAccessStream`için ararsanız, döndürülen tür . `IRandomAccessStream`uygular `IInputStream` ve `IOutputStream`okuma ve yazmayı destekler.

.NET Framework akışları, dönüşümden sonra bile klonlamayı desteklemez. Bir .NET Framework akışını Windows Runtime akışına <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>ve aramasına dönüştürürseniz veya <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>(doğrudan ararsanız) <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> bir özel durum oluşur.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Örnek: .NET Framework'ü Windows Runtime rasgele erişim akışına dönüştürün

.NET Framework akışından Windows Runtime rasgele erişim akışına <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> dönüştürmek için aşağıdaki örnekte gösterildiği gibi yöntemi kullanın:

> [!IMPORTANT]
> Kullandığınız .NET Framework akışının arama yı desteklediğinden emin olun veya bunu yapan bir akışa kopyalayın. Bunu belirlemek <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> için özelliği kullanabilirsiniz.

Bu örneği çalıştırmak için,.NET Framework 4.5.1'i hedefleyen ve adlı `TextBlock2` bir metin bloğu ve `Button2`bir düğme içeren bir UWP XAML uygulaması oluşturun. Düğme tıklatma olayını `button2_Click` örnekte gösterilen yöntemle ilişkilendirin.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlatma: Bir dosyayı okuma ve yazma (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [.NET Windows Mağazası uygulamaları için genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [.NET Windows Mağazası uygulamaları API'leri için](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
