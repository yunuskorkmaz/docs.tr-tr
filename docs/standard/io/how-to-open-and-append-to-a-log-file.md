---
title: 'Nasıl yapılır: günlük dosyasını açma ve ekleme'
description: .NET 'teki StreamWriter ve StreamReader sınıflarını kullanarak bir günlük dosyası açın ve akışlara karakterler yazıp buradan karakter okur.
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
ms.openlocfilehash: a66dadd24cc327824e91df733f11a23112cd384a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769177"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Nasıl yapılır: günlük dosyasını açma ve ekleme
<xref:System.IO.StreamWriter>ve <xref:System.IO.StreamReader> akışlardan karakter yazıp karakterleri okur. Aşağıdaki kod örneği, giriş için *log.txt* dosyasını açar veya yoksa oluşturur ve günlük bilgilerini dosyanın sonuna ekler. Örnek daha sonra dosyanın içeriğini görüntüleme için standart çıktıya yazar.

Bu örneğe alternatif olarak, bilgileri tek bir dize veya dize dizisi olarak saklayabilir ve <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> aynı işlevselliğe ulaşmak için veya yöntemini kullanabilirsiniz.  
  
> [!NOTE]
> Visual Basic kullanıcılar, <xref:Microsoft.VisualBasic.Logging.Log> <xref:Microsoft.VisualBasic.FileIO.FileSystem> günlük dosyalarını oluşturmak veya yazmak için sınıf veya sınıf tarafından sunulan yöntemleri ve özellikleri kullanmayı seçebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](index.md)
