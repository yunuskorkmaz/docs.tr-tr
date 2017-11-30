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
# <a name="composing-streams"></a><span data-ttu-id="a0711-102">Akışlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0711-102">Composing Streams</span></span>
<span data-ttu-id="a0711-103">Bir disk veya bellek gibi bir depolama ortamına bir yedekleme deposudur.</span><span class="sxs-lookup"><span data-stu-id="a0711-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="a0711-104">Her farklı yedekleme deposu uygulaması, kendi akış uygulayan <xref:System.IO.Stream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0711-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="a0711-105">Her akış türü okur ve ilk ve son, belirtilen yedekleme depolama bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="a0711-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="a0711-106">Depoları yedekleme için bağlanmak akışları temel akışlar adı verilir.</span><span class="sxs-lookup"><span data-stu-id="a0711-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="a0711-107">Temel akışlar akış yedekleme deposuna bağlanmak için gereken parametrelere sahip oluşturucular vardır.</span><span class="sxs-lookup"><span data-stu-id="a0711-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="a0711-108">Örneğin, <xref:System.IO.FileStream> dosya işlemleri ve benzeri nasıl paylaşılacak belirten bir yol parametresi belirtin Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="a0711-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="a0711-109">Tasarımını <xref:System.IO> Basitleştirilmiş akışı oluşturma sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0711-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="a0711-110">Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a0711-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="a0711-111">Tercih edilen türleri okuma ya da kolayca yazılmış bir okuyucu veya yazan zinciri sonuna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a0711-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="a0711-112">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="a0711-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="a0711-113">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir <xref:System.IO.StreamReader> karakterlerinden okumak için oluşturulan **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="a0711-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="a0711-114"><xref:System.IO.StreamReader.ReadLine%2A>kadar okur <xref:System.IO.StreamReader.Peek%2A> başka karakter bulur.</span><span class="sxs-lookup"><span data-stu-id="a0711-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="a0711-115">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="a0711-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="a0711-116">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir **BinaryReader** baytlar okumak için oluşturulan **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="a0711-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="a0711-117"><xref:System.IO.BinaryReader.ReadByte%2A>kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla baytı yok bulur.</span><span class="sxs-lookup"><span data-stu-id="a0711-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="a0711-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0711-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
