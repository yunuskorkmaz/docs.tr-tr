---
title: 'Nasıl yapılır: Bir dosyadan metin okuma'
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7330c209ce6514459d3ab1dd58dc1c80b1978a56
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56834959"
---
# <a name="how-to-read-text-from-a-file"></a>Nasıl yapılır: Bir dosyadan metin okuma
Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir. Her iki örnek örneğini oluşturduğunuzda <xref:System.IO.StreamReader> sınıfı, dosyanın göreli veya mutlak yolunu sağlayın. 
  
> [!NOTE]
> Windows çalışma zamanı için dosyaları okuma ve yazma için farklı akış türleri sağladığından Bu kod örnekleri için evrensel Windows (UWP) uygulamaları, geliştirme için geçerli değildir. Bir UWP uygulamasında bir dosyadan metin okuma gösteren bir örnek için bkz: [hızlı başlangıç: Dosyaları okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). .NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme yapılacağını gösteren örnekler için bkz [nasıl yapılır: .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Örnek: Bir konsol uygulamasında zaman uyumlu okuma  
Aşağıdaki örnek bir konsol uygulaması bir zaman uyumlu okuma işlemini gösterir. Bu örnek, bir akış okuyucusunu kullanarak metin dosyasını açar, içeriğini bir dizeye kopyalar ve konsola dizesi çıkarır.  
  
> [!IMPORTANT]
> Örnek adlı bir dosya olduğunu varsayar *TestFile.txt* uygulama ile aynı klasörde zaten mevcut.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Örnek: Bir WPF uygulamasında zaman uyumsuz okuma 
 Aşağıdaki örnek, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz bir okuma işlemini gösterir.  
  
> [!IMPORTANT]
> Örnek adlı bir dosya olduğunu varsayar *TestFile.txt* uygulama ile aynı klasörde zaten mevcut.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Hızlı Başlangıç: Dosyaları okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Nasıl yapılır: .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: Dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: Bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
