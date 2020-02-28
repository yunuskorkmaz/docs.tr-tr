---
title: 'Nasıl yapılır: dizeden karakterleri okuma'
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155769"
---
# <a name="how-to-read-characters-from-a-string"></a>Nasıl yapılır: dizeden karakterleri okuma
Aşağıdaki kod örnekleri, bir dizeden zaman uyumlu veya zaman uyumsuz karakterlerin nasıl okunacağını gösterir.  
  
## <a name="example-read-characters-synchronously"></a>Örnek: karakterleri zaman uyumlu olarak okuyun
 Bu örnek, bir dizeden zaman uyumlu olarak 13 karakter okur, bunları bir dizide depolar ve görüntüler. Örnek daha sonra dizedeki karakterlerin geri kalanını okur, bunları altıncı öğeden başlayarak dizide depolar ve dizinin içeriğini görüntüler.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Örnek: karakterleri zaman uyumsuz olarak oku  
 Sonraki örnek, bir WPF uygulamasının arkasındaki koddur. Pencere yükleme sırasında, örnek zaman uyumsuz olarak bir <xref:System.Windows.Controls.TextBox> denetimindeki tüm karakterleri okur ve bunları bir dizide depolar. Ardından, her bir harfi veya boşluk karakterini <xref:System.Windows.Controls.TextBlock> denetimin ayrı bir satırına zaman uyumsuz olarak yazar.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
