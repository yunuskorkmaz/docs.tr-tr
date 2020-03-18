---
title: 'Nasıl yazılır: Karakterleri bir dize yazma'
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160293"
---
# <a name="how-to-write-characters-to-a-string"></a>Nasıl yazılır: Karakterleri bir dize yazma
Aşağıdaki kod örnekleri, karakterleri eşzamanlı olarak veya bir karakter dizisinden bir dize eşit olarak yazar.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Örnek: Konsol uygulamasına eşzamanlı karakter yazma  
 Aşağıdaki örnek, <xref:System.IO.StringWriter> bir <xref:System.Text.StringBuilder> nesneye eşzamanlı olarak beş karakter yazmak için a kullanır.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Örnek: Karakterleri bir WPF uygulamasına eşzamanlı olarak yazma
 Sonraki örnek, bir WPF uygulamasının arkasındaki koddur. Pencere yükünde, örnek tüm karakterleri denetimden <xref:System.Windows.Controls.TextBox> eşit bir şekilde okur ve bir dizide saklar. Daha sonra eşzamanlı bir denetim ayrı bir satıra <xref:System.Windows.Controls.TextBlock> her harf veya beyaz boşluk karakter yazar.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)  
- [Asynchronous dosya I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Dizinleri ve dosyaları sayısal](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılı: Günlük dosyasını açma ve ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapilir: Dosyadaki metni okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yazılır: Dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapilir: Bir dizedeki karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
