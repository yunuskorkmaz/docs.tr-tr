---
title: Akışlar oluşturma
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950377"
---
# <a name="compose-streams"></a>Akışlar oluşturma
A *yedekleme deposu* disk veya bellek gibi bir depolama Orta'dır. Her farklı yedekleme deposu uygulaması kendi akış uygulayan <xref:System.IO.Stream> sınıfı. 

Her akış türü okur ve Kimden ve Kime, belirtilen yedekleme deposu bayt yazar. Depoları için bağlandığı akışları çağrılır *temel akışları*. Temel akışlar yedekleme deposu için akışa bağlanmak için gereken parametreleri oluşturucularla vardır. Örneğin, <xref:System.IO.FileStream> dosya işlemler tarafından nasıl paylaşılır belirtir bir yol parametresi belirtin Oluşturucusu vardır.  

Tasarımını <xref:System.IO> basitleştirilmiş bir akış oluşturma sınıflar sağlar. Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara ekleyebilirsiniz. Tercih edilen türleri okuma ya da kolayca yazılan okuyucuya veya yazara zinciri sonuna ekleyebilirsiniz.  

Aşağıdaki kod örnekleri oluşturma bir **FILESTREAM** var olan geçici *MyFile.txt* arabellek sırada *MyFile.txt*. Unutmayın **FileStreams** varsayılan olarak ara belleğe alınır.

>[!IMPORTANT]
>Örnekler adlı bir dosya olduğunu varsayar *MyFile.txt* uygulama ile aynı klasörde zaten mevcut.  

## <a name="example-use-streamreader"></a>Örnek: StreamReader kullanın
Aşağıdaki örnek, oluşturur bir <xref:System.IO.StreamReader> karakterleri okumak için **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişken olarak. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> Daha sonra kadar okur <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> başka karakter bulur.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Örnek: BinaryReader kullanın
Aşağıdaki örnek, oluşturur bir <xref:System.IO.BinaryReader> bayt okunacak **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişken olarak. <xref:System.IO.BinaryReader.ReadByte%2A> Daha sonra kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> hiçbir daha fazla bayt bulur.  
  
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
