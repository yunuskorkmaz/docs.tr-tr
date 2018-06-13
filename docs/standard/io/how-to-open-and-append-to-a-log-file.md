---
title: 'Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme'
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
ms.openlocfilehash: cd2d13a49d9b696541ac278b9f1847c8e4a48cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571949"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme
<xref:System.IO.StreamWriter> ve <xref:System.IO.StreamReader> karakterleri yazmak ve akışlardan karakterleri okuma. Aşağıdaki kod örnek açılır `log.txt` dosya için giriş veya zaten mevcut değilse ve bilgi dosyasının sonuna ekler dosyası oluşturur. Ardından dosyasının içeriğini görüntülemek için standart çıktı yazılır. Bu örnek için alternatif olarak, bilgileri tek bir dize veya dize dizisi olarak depolanabilir ve <xref:System.IO.File.WriteAllText%2A> veya <xref:System.IO.File.WriteAllLines%2A> yöntemi aynı işlevselliği elde etmek için kullanılabilir.  
  
> [!NOTE]
>  Visual Basic kullanıcıları tarafından sağlanan özellikler ve yöntemler kullanmayı seçebilir <xref:Microsoft.VisualBasic.Logging.Log> sınıfı veya <xref:Microsoft.VisualBasic.FileIO.FileSystem> oluşturmak veya günlük dosyaları yazma sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Nasıl yapılır: Dosyadan Metin Okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Nasıl yapılır: Dizeden Karakterleri Okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Nasıl yapılır: Bir Dizeye Karakter Yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
