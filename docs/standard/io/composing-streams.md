---
title: Akışları oluştur
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
ms.openlocfilehash: 689cc9537cd7a5fe6a677d42e5790bbcf1b3aefa
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708154"
---
# <a name="compose-streams"></a>Akışları oluştur
*Yedekleme deposu* , disk veya bellek gibi bir depolama ortamıdır. Her farklı yedekleme deposu, <xref:System.IO.Stream> sınıfının bir uygulama olarak kendi akışını uygular. 

Her akış türü, ve ' den verilen yedekleme deposundan baytları okur ve yazar. Yedekleme depolarına bağlanan akışlar *Temel akışlar*olarak adlandırılır. Temel akışlar, akışı yedekleme deposuna bağlamak için gereken parametrelere sahip oluşturucuları vardır. Örneğin, <xref:System.IO.FileStream>, dosyanın işlemlerle nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturuculara sahiptir.  

<xref:System.IO> sınıflarının tasarımı Basitleştirilmiş akış oluşturmayı sağlar. Temel akışları, istediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışlarına ekleyebilirsiniz. Zincirin sonuna bir okuyucu veya yazıcı ekleyebilirsiniz, böylece tercih edilen türler kolayca okunabilir veya yazılabilir.  

Aşağıdaki kod örnekleri, *Dosyam. txt*' i arabelleğe almak Için mevcut *Dosyam. txt* etrafında bir **FILESTREAM** oluşturur. **FileStreams** varsayılan olarak arabelleğe alınır ' i unutmayın.

>[!IMPORTANT]
>Örneklerde, *Dosyam. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten varolduğu varsayılır.  

## <a name="example-use-streamreader"></a>Örnek: StreamReader kullanın
Aşağıdaki örnek, bir ' ın Oluşturucu bağımsız değişkeni olarak **StreamReader** 'a geçirildiği, **FILESTREAM**'ten karakter okumak için bir <xref:System.IO.StreamReader> oluşturur. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>, <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> daha fazla karakter bulana kadar okur.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Örnek: BinaryReader kullanın
Aşağıdaki örnek, Oluşturucu bağımsız değişkeni olarak **BinaryReader** 'a geçirilen, **FILESTREAM**'ten bayt okumak için bir <xref:System.IO.BinaryReader> oluşturur. <xref:System.IO.BinaryReader.ReadByte%2A>, <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla bayt bulana kadar okur.  
  
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
