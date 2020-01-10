---
title: 'Nasıl yapılır: dosyadan metin okuma'
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
ms.openlocfilehash: 49ea989a2b11c6572dc08970cf96e2df5f4fa024
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706666"
---
# <a name="how-to-read-text-from-a-file"></a>Nasıl yapılır: dosyadan metin okuma
Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir. Her iki örnekte de, <xref:System.IO.StreamReader> sınıfının örneğini oluşturduğunuzda, dosyanın göreli veya mutlak yolunu sağlarsınız. 
  
> [!NOTE]
> Bu kod örnekleri, Evrensel Windows (UWP) uygulamaları için geliştirilmez, çünkü Windows Çalışma Zamanı dosyalara okuma ve yazma için farklı akış türleri sağlar. UWP uygulamasında bir dosyadaki metnin nasıl okunacağını gösteren bir örnek için bkz. [hızlı başlangıç: dosya okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında nasıl dönüştürme yapılacağını gösteren örnekler için bkz. [nasıl yapılır: .NET Framework akışlar ve Windows çalışma zamanı akışları arasında dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Örnek: konsol uygulamasında zaman uyumlu okuma  
Aşağıdaki örnek, bir konsol uygulaması içinde zaman uyumlu okuma işlemini gösterir. Bu örnek, bir akış okuyucusu kullanarak metin dosyasını açar, içeriği bir dizeye kopyalar ve dizeyi konsola verir.  
  
> [!IMPORTANT]
> Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Örnek: WPF uygulamasında zaman uyumsuz okuma 
 Aşağıdaki örnek, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemini gösterir.  
  
> [!IMPORTANT]
> Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Hızlı başlangıç: dosyaları okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Nasıl yapılır: .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
