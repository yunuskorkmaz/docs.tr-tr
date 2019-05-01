---
title: 'Nasıl yapılır: Dizeden karakterleri okuma'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947192"
---
# <a name="how-to-read-characters-from-a-string"></a>Nasıl yapılır: Dizeden karakterleri okuma
Aşağıdaki kod örnekleri, zaman uyumlu veya zaman uyumsuz olarak bir dizeden karakterleri okuma işlemini göstermektedir.  
  
## <a name="example-read-characters-synchronously"></a>Örnek: Zaman uyumlu olarak karakterleri okuma 
 Bu örnekte 13 karakter zaman uyumlu bir dizeden, bunları bir dizide saklar ve bunları görüntüler okur. Örnek daha sonra geri kalanı dize içindeki karakter okur, altıncı öğe başlangıç dizisi depolar ve dizinin içeriğini görüntüler.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Örnek: Zaman uyumsuz olarak karakterleri okuma  
 Sonraki örnekte, bir WPF uygulaması arka plan kod bulunur. Penceresi yüklendiğinde örnek zaman uyumsuz olarak tüm karakterleri okur. bir <xref:System.Windows.Controls.TextBox> denetleyebilir ve bunları bir dizide saklar. Bunu sonra zaman uyumsuz olarak her bir harf veya boşluk karakteri ayrı bir satır yazan bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılır: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: Bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
