---
title: 'Nasıl yapılır: Bir dizeye karakter yazma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947101"
---
# <a name="how-to-write-characters-to-a-string"></a>Nasıl yapılır: Bir dizeye karakter yazma
Aşağıdaki kod örnekleri karakter zaman uyumlu veya zaman uyumsuz olarak bir karakter dizisinden bir dize olarak yazın.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Örnek: Karakterleri bir konsol uygulamasında zaman uyumlu olarak yazma  
 Aşağıdaki örnekte bir <xref:System.IO.StringWriter> beş karakteri çok zaman uyumlu olarak yazmak için bir <xref:System.Text.StringBuilder> nesne. 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Örnek: Karakterleri bir WPF uygulamasında zaman uyumsuz olarak yazar. 
 Sonraki örnekte, bir WPF uygulaması arka plan kod bulunur. Penceresi yüklendiğinde örnek zaman uyumsuz olarak tüm karakterleri okur. bir <xref:System.Windows.Controls.TextBox> denetleyebilir ve bunları bir dizide saklar. Bunu sonra zaman uyumsuz olarak her bir harf veya boşluk karakteri ayrı bir satır yazan bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: Dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
