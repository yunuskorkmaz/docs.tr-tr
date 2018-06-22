---
title: 'Nasıl yapılır: Dosyadan Metin Okuma'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7c54e5e55770f3df44819cdf6d2d2c866f7e0fc
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298168"
---
# <a name="how-to-read-text-from-a-file"></a>Nasıl yapılır: Dosyadan Metin Okuma
Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir. Örneğini oluştururken hem örneklerde <xref:System.IO.StreamReader> sınıfı, dosya için göreli veya mutlak yol sağlayın. Aşağıdaki örnek, uygulamayla aynı klasörde TestFile.txt adında bir dosya bulunduğunu kabul eder.  
  
 Bu kod örnekleri Windows çalışma zamanı dosyaları için okuma ve yazma için farklı akış türleri sağladığından için Windows mağazası uygulamaları geliştirmek için geçerli değildir. Bir Windows mağazası uygulamasında bir dosyadan metin okuma gösteren örnek için bkz: [hızlı başlangıç: Okuma ve dosyalara yazma](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)). .NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme Göster örnekler için bkz: [nasıl yapılır: .NET Framework akışları arasında dönüştürme ve Windows çalışma zamanı akışları](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir konsol uygulaması içinde eşzamanlı okuma işlemi gösterir. Bu örnekte, metin dosyası kullanarak bir akış okuyucusunu açıldığında, içeriği bir dizeye kopyalanır ve konsola çıktı dizedir.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemi gösterilmektedir.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Nasıl yapılır: bir dizin listesi oluşturma](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Hızlı Başlangıç: Okuma ve dosyalara yazma](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Nasıl yapılır: Dizeden Karakterleri Okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Nasıl yapılır: Bir Dizeye Karakter Yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
