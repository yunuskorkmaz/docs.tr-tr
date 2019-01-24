---
title: 'Nasıl yapılır: Dizeden karakterleri okuma'
ms.date: 03/30/2017
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
ms.openlocfilehash: cbf213c783d1688e9168265cedc27d2ac7a5a96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504823"
---
# <a name="how-to-read-characters-from-a-string"></a>Nasıl yapılır: Dizeden karakterleri okuma
Aşağıdaki kod örnekleri, zaman uyumlu ve zaman uyumsuz olarak bir dizeden karakterleri okuma işlemini göstermektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte 13 karakter zaman uyumlu olarak dize, bunları bir dizide saklar ve bu karakterleri okur. Ardından kalan karakter dizesini okur, altıncı öğe başlangıç dizisi depolar ve dizinin içeriğini görüntüler.  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, zaman uyumsuz olarak öğesindeki tüm karakterleri okur bir <xref:System.Windows.Controls.TextBox> denetlemek ve bunları bir dizide saklar. Ardından zaman uyumsuz olarak her bir harf veya boşluk karakteri için bir satır sonu ardından ayrı bir satırda Yazar bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringReader>
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>
- [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)
- [NIB: Nasıl yapılır: Create a Directory Listing](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [Nasıl yapılır: Bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
