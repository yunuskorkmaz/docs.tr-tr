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
ms.openlocfilehash: 3f18712793254f4942c092c87a3e64c73b492ae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160111"
---
# <a name="compose-streams"></a>Akışlar oluşturma
*Destek deposu,* disk veya bellek gibi bir depolama ortamıdır. Her farklı destek deposu <xref:System.IO.Stream> sınıfın bir uygulaması olarak kendi akışını uygular.

Her akış türü, verilen destek deposundan baytları okur ve yazar. Destek depolarına bağlanan akışlara *temel akış*denir. Temel akışlarda, akışı destek deposuna bağlamak için gerekli parametrelere sahip yapıcılar vardır. Örneğin, <xref:System.IO.FileStream> dosyanın işlemler tarafından nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturucular vardır.  

<xref:System.IO> Sınıfların tasarımı basitleştirilmiş akış kompozisyonu sağlar. İstediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışına temel akışlar ekleyebilirsiniz. Tercih edilen türleri kolayca okunabilir veya yazılabilir, böylece zincirin sonuna bir okuyucu veya yazar ekleyebilirsiniz.  

Aşağıdaki kod örnekleri *MyFile.txt'yi*arabelleğe almak için varolan *MyFile.txt'nin* etrafında bir **FileStream** oluşturur. **FileStreams** varsayılan olarak arabelleğe olduğunu unutmayın.

>[!IMPORTANT]
>Örnekler, *MyFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten mevcut olduğunu varsayar.  

## <a name="example-use-streamreader"></a>Örnek: StreamReader'ı kullanın
Aşağıdaki örnek, oluşturan <xref:System.IO.StreamReader> bağımsız değişken olarak **StreamReader'a** geçirilen **FileStream'den**okunacak karakterler oluşturur. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>sonra başka <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> karakter bulana kadar okur.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Örnek: BinaryReader kullanın
Aşağıdaki örnek, kurucu <xref:System.IO.BinaryReader> bağımsız değişkeni olarak **BinaryReader'a** geçirilen **FileStream'den**okunacak baytlar oluşturur. <xref:System.IO.BinaryReader.ReadByte%2A>sonra daha <xref:System.IO.BinaryReader.PeekChar%2A> fazla bayt bulana kadar okur.  
  
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
