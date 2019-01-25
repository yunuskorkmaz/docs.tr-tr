---
title: 'Nasıl yapılır: .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a006d739b6fa9a31ad238702dd0b2d26254deca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492772"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Nasıl yapılır: .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüştürme

Windows Mağazası için .NET Framework uygulamaları tam .NET Framework'ün bir alt kümesidir. Windows Mağazası uygulamaları için güvenlik ve diğer gereksinimler nedeniyle, .NET Framework API'ların tam kümesini dosyaları açmak ve okumak için kullanamazsınız. Daha fazla bilgi için [.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışları işlemek için bunu bir .NET Framework akış türü arasında dönüştürme yapmayı gerekli bulabilirsiniz <xref:System.IO.MemoryStream> veya <xref:System.IO.FileStream>ve bir Windows çalışma zamanı akışına gibi <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, veya <xref:Windows.Storage.Streams.IRandomAccessStream>.

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) sınıfı bu dönüştürmeleri kolaylaştıran yöntemler içerir. Ancak, .NET Framework ve Windows Çalışma Zamanı'nda bu yöntemlerin kullanılmasının sonuçlarını etkileyecek temel farklar vardır. Ayrıtılar aşağıdaki bölümlerde açıklanmıştır.

## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı akışından bir .NET Framework akışına dönüştürme

Aşağıdakilerden birini kullanarak bir Windows çalışma zamanı akışından bir .NET Framework akışına dönüştürebilirsiniz [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) yöntemleri:

[System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx)  
Windows Çalışma Zamanı'ndaki rastgele erişimli bir akışı, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx)  
Windows Çalışma Zamanı'ndaki bir çıkış akışını, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx)  
Windows Çalışma Zamanı'ndaki bir giriş akışını, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.

Windows Çalışma Zamanı, yalnızca okumayı, yalnızca yazmayı veya okumayı ve yazmayı destekleyen akış türleri sunar ve bir Windows Çalışma Zamanı akışını bir .NET Framework akışına dönüştürdüğünüzde bu yetenekler korunur. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız. Dönüştürmek istediğiniz Windows Çalışma Zamanı akışının yetenekleriyle eşleşen dönüştürme yöntemini kullanmak en iyi uygulamadır. Ancak, bu yana <xref:Windows.Storage.Streams.IRandomAccessStream> okunabilir ve yazılabilir olduğundan (hem <xref:Windows.Storage.Streams.IOutputStream> ve <xref:Windows.Storage.Streams.IInputStream>, dönüştürme yöntemlerinden herhangi birini kullanabilirsiniz ve özgün akışın yetenekleri korunur. Örneğin, kullanarak [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) dönüştürmek için bir <xref:Windows.Storage.Streams.IRandomAccessStream> dönüştürülen .NET Framework akışını yalnızca okunabilir olması için sınırlamaz; ayrıca yazılabilir de.

### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı rastgele erişimli akışından bir .NET Framework akışına dönüştürmek için

- Kullanım [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) yöntemi.

  Aşağıdaki kod örneğinde, bir kullanıcıdan bir dosya seçmesinin, dosyayı Windows Çalışma Zamanı API'ları ile açmasının ve sonra dosyayı okunan ve bir metin bloğuna çıkışı yapılan bir .NET Framework akışına dönüştürmesinin nasıl isteneceği gösterilmektedir. Bu senaryoda, sonuçların çıktısını almadan önce, genellikle akışı .NET Framework API'ları ile akış işlersiniz.

  Bu örneği çalıştırmak için adlı bir metin bloğu içeren bir Windows Store XAML uygulaması oluşturmanız gerekir `TextBlock1` adlı bir düğme `Button1`. Düğmesini olay ilişkilendirilmelidir `button1_Click` örnekte gösterilen yöntemi.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]

## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Bir .NET Framework akışından bir Windows Çalışma Zamanı akışına dönüştürme

Aşağıdakilerden birini kullanarak bir .NET Framework akışından bir Windows çalışma zamanı akışına dönüştürebilirsiniz [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) yöntemleri:

[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) .NET için Windows Store uygulamaları altkümesindeki yönetilen bir akışı, Windows çalışma zamanı'ndaki bir giriş akışına dönüştürür.

[System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) Windows çalışma zamanı'ndaki bir çıkış akışına .NET için Windows Store uygulamaları altkümesindeki yönetilen bir akışa dönüştürür.

[AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) .NET için Windows Store uygulamaları altkümesindeki yönetilen bir akışı okuma veya yazma Windows çalışma zamanı için kullanılabilecek bir rastgele erişim akışına dönüştürür.

Bir .NET Framework akışını bir Windows Çalışma Zamanı akışına dönüştürdüğünüzde, dönüştürülen akışın yetenekleri özgün akışa bağlı olacaktır. Örneğin, özgün akışını hem okuma hem yazma destekliyorsa ve çağırmanızı[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) döndürülen türü olacaktır ve akışı dönüştürmek için bir `IRandomAccessStream`, uygulayan `IInputStream` ve `IOutputStream`ve okuma ve yazmayı destekler.

.NET Framework akışları, dönüştürmeden sonra bile klonlamayı desteklemez. Bir Windows çalışma zamanı akışına ve çağrısı için bir .NET Framework akışına dönüştürürseniz, bunun anlamı <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> veya <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, hangi çağrı <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> veya çağrı <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> doğrudan bir özel durum oluşur.

### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Bir .NET Framework akışından bir Windows Çalışma Zamanı rastgele erişim akışına dönüştürmek için

- Kullanım [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) aşağıdaki örnekte gösterildiği gibi yöntemi:

  > [!IMPORTANT]
  > Kullanmakta olduğunuz .NET Framework akışının aramayı desteklediğinden emin olun veya onu destekleyen bir akışa kopyalayın. Kullanabileceğiniz <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> bunu belirlemek için özellik.

  Bu örneği çalıştırmak için .NET Framework 4.5.1'i hedefleyen ve adlı bir metin bloğu içeren bir Windows Store XAML uygulaması oluşturmanız gerekir `TextBlock2` adlı bir düğme `Button2`. Düğmesini olay ilişkilendirilmelidir `button2_Click` Bu örnekte gösterilen yöntemi.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Okuma ve yazma dosya (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)
- [.NET için Windows Store uygulamalarına genel bakış](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)
- [.NET için Windows Store uygulamaları – desteklenen API'ler](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)
