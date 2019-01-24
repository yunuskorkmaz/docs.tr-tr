---
title: 'Nasıl yapılır: Bir dizeye karakter yazma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740989"
---
# <a name="how-to-write-characters-to-a-string"></a>Nasıl yapılır: Bir dizeye karakter yazma
Aşağıdaki kod örnekleri karakter zaman uyumlu ve zaman uyumsuz olarak bir karakter dizisinden bir dize olarak yazın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek 5 karakter dizisinden zaman uyumlu bir dizeye yazar.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, zaman uyumsuz olarak öğesindeki tüm karakterleri okur bir <xref:System.Windows.Controls.TextBox> denetlemek ve bunları bir dizide saklar. Ardından zaman uyumsuz olarak her bir harf veya boşluk karakteri için bir satır sonu ardından ayrı bir satırda Yazar bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)
- [Nasıl yapılır: Dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [Nasıl yapılır: Dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
