---
title: Akışları oluştur
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
ms.openlocfilehash: d848a989378ed40df794554f3a0a9a7f135fbd4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732196"
---
# <a name="compose-streams"></a>Akışları oluştur

*Yedekleme deposu* , disk veya bellek gibi bir depolama ortamıdır. Her farklı yedekleme deposu, sınıfının bir uygulama olarak kendi akışını uygular <xref:System.IO.Stream> .

Her akış türü, ve ' den verilen yedekleme deposundan baytları okur ve yazar. Yedekleme depolarına bağlanan akışlar *Temel akışlar* olarak adlandırılır. Temel akışlar, akışı yedekleme deposuna bağlamak için gereken parametrelere sahip oluşturucuları vardır. Örneğin, <xref:System.IO.FileStream> dosyanın işlemlerle nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturucular vardır.  

<xref:System.IO>Sınıfların tasarımı Basitleştirilmiş akış kompozisyonu sağlar. Temel akışları, istediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışlarına ekleyebilirsiniz. Zincirin sonuna bir okuyucu veya yazıcı ekleyebilirsiniz, böylece tercih edilen türler kolayca okunabilir veya yazılabilir.  

Aşağıdaki kod örnekleri, *MyFile.txt* arabelleğe almak için mevcut *MyFile.txt* etrafında bir **FILESTREAM** oluşturur. **FileStreams** varsayılan olarak arabelleğe alınır ' i unutmayın.

>[!IMPORTANT]
>Örnekler, *MyFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.  

## <a name="example-use-streamreader"></a>Örnek: StreamReader kullanın

Aşağıdaki örnek, bir <xref:System.IO.StreamReader> ' ın Oluşturucu bağımsız değişkeni olarak **StreamReader** 'A geçirilmiş olan **FILESTREAM**'ten okuma karakterleri oluşturur. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> ardından, <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> daha fazla karakter bulana kadar okur.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Örnek: BinaryReader kullanın

Aşağıdaki örnek, <xref:System.IO.BinaryReader> Oluşturucu bağımsız değişkeni olarak **BinaryReader** 'A geçirilmiş olan **FILESTREAM**'ten baytları okumak için bir, oluşturur. <xref:System.IO.BinaryReader.ReadByte%2A> ardından, <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla bayt bulana kadar okur.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
