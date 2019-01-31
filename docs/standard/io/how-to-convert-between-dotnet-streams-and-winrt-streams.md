---
title: 'Nasıl yapılır: .NET Framework ve Windows çalışma zamanı arasında akışları (yalnızca Windows) dönüştürme'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc38e69a79af7c7220b8e3b55d4cb1f4ca3695f6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255204"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Nasıl yapılır: .NET Framework ve Windows çalışma zamanı arasında akışları (yalnızca Windows) dönüştürme

UWP uygulamaları için .NET Framework, tam .NET Framework'ün bir alt kümesidir. Güvenlik ve UWP uygulamaları için diğer gereksinimleri nedeniyle, .NET Framework API kümesini dosyaları açmak ve okumak için kullanamazsınız. Daha fazla bilgi için [.NET UWP uygulamalarına genel bakış için](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışları işlemek için bir .NET Framework akış türü arasında gibi dönüştürebilirsiniz <xref:System.IO.MemoryStream> veya <xref:System.IO.FileStream>ve bir Windows çalışma zamanı akışına gibi <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, veya <xref:Windows.Storage.Streams.IRandomAccessStream>.

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) sınıfı bu dönüştürmeleri kolaylaştıran yöntemler içerir. Ancak, .NET Framework ve Windows çalışma zamanı akışları arasındaki temeldeki farklar aşağıdaki bölümlerde açıklandığı gibi bu yöntemlerin sonuçları etkiler:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Bir Windows çalışma zamanını şuradan bir .NET Framework akışına dönüştürme
Bir Windows çalışma zamanı akışından bir .NET Framework akışına dönüştürmek için aşağıdakilerden birini kullanın: [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) yöntemleri:

- [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) UWP uygulamaları için .NET içinde yönetilen bir akışa bir Windows çalışma zamanı rastgele erişim akışına dönüştürür.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx) Windows çalışma zamanı'ndaki bir çıkış akışına UWP uygulamaları için .NET içinde yönetilen bir akışa dönüştürür.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) .NET içinde yönetilen bir akışa UWP uygulamaları için Windows çalışma zamanı'ndaki bir giriş akışına dönüştürür.

Windows çalışma zamanı yalnızca okuma, yalnızca, yazmayı veya okumayı ve yazmayı destekleyen akış türleri sunar. Bir Windows çalışma zamanı akışını bir .NET Framework akışına dönüştürdüğünüzde bu yetenekler korunur. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız. 

Dönüştürmek istediğiniz Windows çalışma zamanı akışın yetenekleri eşleşen dönüştürme yöntemini kullanmak iyi bir uygulamadır. Ancak, bu yana <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir ve yazılabilir olduğundan (hem <xref:Windows.Storage.Streams.IOutputStream> ve <xref:Windows.Storage.Streams.IInputStream>), özgün akışın yetenekleri dönüştürme yöntemleri sağlamak. Örneğin, kullanarak [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) dönüştürmek için bir <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir olmanın dönüştürülen .NET Framework akışına kısıtlamaz. Yazılabilir.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Örnek: Windows çalışma zamanı rastgele erişimli .NET Framework akışına dönüştürme
Bir Windows çalışma zamanı rastgele erişimli akışından bir .NET Framework akışına dönüştürmek için kullanın [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) yöntemi.

Aşağıdaki kod örneğinde bir dosya seçmenizi ister, Windows çalışma zamanı API'leri ile açar ve ardından bir .NET Framework akışına dönüştürür. Bu akışı okur ve bir metin bloğuna çıkışı. Genellikle sonuç çıktısı önce .NET Framework API'ları ile akış işleme.

Bu örneği çalıştırmak için adlı bir metin bloğu içeren bir UWP XAML uygulaması oluşturmanız `TextBlock1` adlı bir düğme `Button1`. İlişkilendirme düğme tıklatma olayını ile `button1_Click` örnekte gösterilen yöntemi.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>.NET Framework'den bir Windows çalışma zamanı akışına dönüştürme
Bir .NET Framework akışından bir Windows çalışma zamanı akışına dönüştürmek için aşağıdakilerden birini kullanın: [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) yöntemleri:

- [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) UWP uygulamaları için yönetilen bir akışı .NET içinde Windows çalışma zamanı'ndaki bir giriş akışına dönüştürür.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) UWP uygulamaları için yönetilen bir akışı .NET içinde Windows çalışma zamanı'ndaki bir çıkış akışına dönüştürür.
  
- [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) UWP uygulamaları için yönetilen bir akışı .NET içinde Windows çalışma zamanı okuma veya yazma için kullanabileceğiniz bir rastgele erişim akışına dönüştürür.

.NET Framework akışını bir Windows çalışma zamanı akışına dönüştürdüğünüzde, dönüştürülen akışın yetenekleri özgün akışa bağlı. Örneğin, özgün akışını hem okuma hem yazma destekliyorsa ve çağırmanızı [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) ve akışı dönüştürmek için döndürülen türdür bir `IRandomAccessStream`. `IRandomAccessStream` uygulayan `IInputStream` ve `IOutputStream`ve okuma ve yazmayı destekler.

.NET framework akışları, dönüştürmeden sonra bile klonlamayı desteklemez. Bir Windows çalışma zamanı akışına ve çağrısı için bir .NET Framework akışına dönüştürürseniz <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> veya <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, hangi çağrı <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, ya da Eğer <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> doğrudan, özel durum oluşur.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Örnek: .NET Framework Windows çalışma zamanı rastgele erişim akışına dönüştürür.

Bir .NET Framework akışından bir Windows çalışma zamanı rastgele erişim akışına dönüştürmek için kullanın [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) aşağıdaki örnekte gösterildiği gibi yöntemi:

> [!IMPORTANT]
> Kullanmakta olduğunuz .NET Framework akışının aramayı desteklediğinden emin olun veya yapan bir akışa kopyalayın. Kullanabileceğiniz <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> bunu belirlemek için özellik.

Bu örneği çalıştırmak için adlı bir metin bloğu içerir ve .NET Framework 4.5.1'i hedefleyen bir UWP XAML uygulaması oluşturmanız `TextBlock2` adlı bir düğme `Button2`. İlişkilendirme düğme tıklatma olayını ile `button2_Click` örnekte gösterilen yöntemi.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Okuma ve yazma dosya (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
- [.NET için Windows Store uygulamalarına genel bakış](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
- [Windows Store uygulamaları için .NET: Desteklenen API'ler](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  
