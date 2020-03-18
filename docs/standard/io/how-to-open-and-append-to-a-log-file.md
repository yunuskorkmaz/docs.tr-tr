---
title: 'Nasıl yapılı: Günlük dosyasını açma ve ekle'
ms.date: 01/21/2019
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
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155717"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Nasıl yapılı: Günlük dosyasını açma ve ekle
<xref:System.IO.StreamWriter>ve <xref:System.IO.StreamReader> karakterleryazmak ve akışları karakterleri okuyun. Aşağıdaki kod örneği giriş için *log.txt* dosyasını açar veya yoksa oluşturur ve günlük bilgilerini dosyanın sonuna ekler. Örnek daha sonra dosyanın içeriğini görüntülemek için standart çıktıya yazar.

Bu örneğe alternatif olarak, bilgileri tek bir dize veya dize <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> dizisi olarak depolayabilir ve aynı işlevselliği elde etmek için veya yöntemi kullanabilirsiniz.  
  
> [!NOTE]
> Visual Basic kullanıcıları, dosyaları oluşturmak veya yazmak <xref:Microsoft.VisualBasic.Logging.Log> için <xref:Microsoft.VisualBasic.FileIO.FileSystem> sınıf veya sınıf tarafından sağlanan yöntemleri ve özellikleri kullanmayı seçebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Nasıl yapılır: Dizinleri ve dosyaları sayısal](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapilir: Dosyadaki metni okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yazılır: Dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapilir: Bir dizedeki karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yazılır: Karakterleri bir dize yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
