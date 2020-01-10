---
title: 'Nasıl yapılır: günlük dosyasını açma ve ekleme'
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
ms.openlocfilehash: b0e399ba3c0cfa0ad3b92afbc7e07af7659e8ae6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706718"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Nasıl yapılır: günlük dosyasını açma ve ekleme
<xref:System.IO.StreamWriter> ve <xref:System.IO.StreamReader> akışlardan karakter yazma ve okuma. Aşağıdaki kod örneği, giriş için *log. txt* dosyasını açar veya yoksa oluşturur ve günlük bilgilerini dosyanın sonuna ekler. Örnek daha sonra dosyanın içeriğini görüntüleme için standart çıktıya yazar. 

Bu örneğe alternatif olarak, bilgileri tek bir dize veya dize dizisi olarak saklayabilir ve aynı işlevselliğe ulaşmak için <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ya da <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.  
  
> [!NOTE]
> Visual Basic kullanıcılar, <xref:Microsoft.VisualBasic.Logging.Log> sınıfı veya <xref:Microsoft.VisualBasic.FileIO.FileSystem> sınıfı tarafından sunulan yöntemleri ve özellikleri günlük dosyaları oluşturmak veya yazmak için kullanmayı seçebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
