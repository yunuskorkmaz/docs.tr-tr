---
title: 'Nasıl yapılır: bir dizeye karakter yazma'
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
ms.openlocfilehash: b53513ef0b373cdde7703eddcd182ab7fd15cb9b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706627"
---
# <a name="how-to-write-characters-to-a-string"></a>Nasıl yapılır: bir dizeye karakter yazma
Aşağıdaki kod örnekleri, bir karakter dizisinden dize içine zaman uyumlu veya zaman uyumsuz karakterler yazar.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Örnek: bir konsol uygulamasında karakterleri eşzamanlı olarak yazma  
 Aşağıdaki örnek, bir <xref:System.Text.StringBuilder> nesnesine beş karakter eşzamanlı olarak yazmak için bir <xref:System.IO.StringWriter> kullanır. 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Örnek: bir WPF uygulamasında karakterleri zaman uyumsuz olarak yazma 
 Sonraki örnek, bir WPF uygulamasının arkasındaki koddur. Pencere yükleme sırasında, örnek zaman uyumsuz olarak bir <xref:System.Windows.Controls.TextBox> denetimindeki tüm karakterleri okur ve bunları bir dizide depolar. Ardından, her bir harfi veya boşluk karakterini <xref:System.Windows.Controls.TextBlock> denetimin ayrı bir satırına zaman uyumsuz olarak yazar.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
