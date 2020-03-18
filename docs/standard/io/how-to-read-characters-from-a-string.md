---
title: 'Nasıl yapilir: Bir dizedeki karakterleri okuma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155769"
---
# <a name="how-to-read-characters-from-a-string"></a>Nasıl yapilir: Bir dizedeki karakterleri okuma
Aşağıdaki kod örnekleri, karakterlerin eşzamanlı olarak veya bir dizeden eşzamanlı olarak nasıl okunduğunu gösterir.  
  
## <a name="example-read-characters-synchronously"></a>Örnek: Karakterleri eşzamanlı olarak okuyun
 Bu örnek, bir dizeden eşzamanlı olarak 13 karakter okur, bunları bir dizide saklar ve görüntüler. Örnek daha sonra dizedeki karakterlerin geri kalanını okur, altıncı öğeden başlayarak dizide saklar ve dizinin içeriğini görüntüler.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Örnek: Karakterleri eşzamanlı olarak okuyun  
 Sonraki örnek, bir WPF uygulamasının arkasındaki koddur. Pencere yükünde, örnek tüm karakterleri denetimden <xref:System.Windows.Controls.TextBox> eşit bir şekilde okur ve bir dizide saklar. Daha sonra eşzamanlı bir denetim ayrı bir satıra <xref:System.Windows.Controls.TextBlock> her harf veya beyaz boşluk karakter yazar.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Asynchronous dosya I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılsın: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılı: Günlük dosyasını açma ve ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapilir: Dosyadaki metni okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yazılır: Dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yazılır: Karakterleri bir dize yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
