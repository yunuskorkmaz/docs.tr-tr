---
title: "Akışlar Oluşturma"
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
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a>Akışlar Oluşturma
Bir disk veya bellek gibi bir depolama ortamına bir yedekleme deposudur. Her farklı yedekleme deposu uygulaması, kendi akış uygulayan <xref:System.IO.Stream> sınıfı. Her akış türü okur ve ilk ve son, belirtilen yedekleme depolama bayt yazar. Depoları yedekleme için bağlanmak akışları temel akışlar adı verilir. Temel akışlar akış yedekleme deposuna bağlanmak için gereken parametrelere sahip oluşturucular vardır. Örneğin, <xref:System.IO.FileStream> dosya işlemleri ve benzeri nasıl paylaşılacak belirten bir yol parametresi belirtin Oluşturucusu vardır.  
  
 Tasarımını <xref:System.IO> Basitleştirilmiş akışı oluşturma sınıflar sağlar. Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara eklenebilir. Tercih edilen türleri okuma ya da kolayca yazılmış bir okuyucu veya yazan zinciri sonuna eklenebilir.  
  
 Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`. (Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir <xref:System.IO.StreamReader> karakterlerinden okumak için oluşturulan **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişkeni olarak. <xref:System.IO.StreamReader.ReadLine%2A>kadar okur <xref:System.IO.StreamReader.Peek%2A> başka karakter bulur.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`. (Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir **BinaryReader** baytlar okumak için oluşturulan **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişkeni olarak. <xref:System.IO.BinaryReader.ReadByte%2A>kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla baytı yok bulur.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
