---
title: 'Nasıl yapılır: Açın ve bir günlük dosyasına Ekle'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 351daa2a13c4a8c4b1551ce74d2eaa6d032f1f17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622743"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Nasıl yapılır: Açın ve bir günlük dosyasına Ekle
<xref:System.IO.StreamWriter> ve <xref:System.IO.StreamReader> akışlardan karakterleri okuma ve yazma karakter. Aşağıdaki kod örneği açılır `log.txt` giriş dosyasını veya zaten mevcut değilse ve dosyanın sonuna bilgi ekler dosyası oluşturur. Dosyanın içeriğini görüntülemek için standart çıktıya ardından yazılır. Bu örnek için alternatif olarak, bilgileri tek bir dize veya dize dizisi olarak depolanabilir ve <xref:System.IO.File.WriteAllText%2A> veya <xref:System.IO.File.WriteAllLines%2A> yöntemi, aynı işlevselliği elde etmek için kullanılabilir.  
  
> [!NOTE]
>  Visual Basic kullanıcıları tarafından sağlanan özellikler ve yöntemler kullanmayı seçebilir <xref:Microsoft.VisualBasic.Logging.Log> sınıfı veya <xref:Microsoft.VisualBasic.FileIO.FileSystem> oluşturmak veya günlük dosyaları yazma sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:System.IO.StreamReader>
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [Nasıl yapılır: Dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
- [Nasıl yapılır: Bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
