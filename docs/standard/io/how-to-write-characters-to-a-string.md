---
title: "Nasıl yapılır: Bir Dizeye Karakter Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a>Nasıl yapılır: Bir Dizeye Karakter Yazma
Aşağıdaki kod örnekleri karakter zaman uyumlu ve zaman uyumsuz olarak karakter dizisinden bir dize olarak yazın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek 5 karakter dizeye dizisinden zaman uyumlu olarak yazar.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte tüm karakterler zaman uyumsuz olarak okur bir <xref:System.Windows.Controls.TextBox> denetleyen ve bunları bir dizide depolar. Ardından zaman uyumsuz olarak her harf ya da boşluk karakteri bir satır sonu arkasından ayrı bir satırda Yazar bir <xref:System.Windows.Controls.TextBlock> denetim.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [Dosya ve akış t-O](../../../docs/standard/io/index.md)  
 [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Nasıl yapılır: açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Nasıl yapılır: bir dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
