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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d49661e93675b80bcd579a6cd341b3dc88a688c2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="composing-streams"></a><span data-ttu-id="4fe4c-102">Akışlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fe4c-102">Composing Streams</span></span>
<span data-ttu-id="4fe4c-103">Bir disk veya bellek gibi bir depolama ortamına bir yedekleme deposudur.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="4fe4c-104">Her farklı yedekleme deposu uygulaması, kendi akış uygulayan <xref:System.IO.Stream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="4fe4c-105">Her akış türü okur ve ilk ve son, belirtilen yedekleme depolama bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="4fe4c-106">Depoları yedekleme için bağlanmak akışları temel akışlar adı verilir.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="4fe4c-107">Temel akışlar akış yedekleme deposuna bağlanmak için gereken parametrelere sahip oluşturucular vardır.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="4fe4c-108">Örneğin, <xref:System.IO.FileStream> dosya işlemleri ve benzeri nasıl paylaşılacak belirten bir yol parametresi belirtin Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="4fe4c-109">Tasarımını <xref:System.IO> Basitleştirilmiş akışı oluşturma sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="4fe4c-110">Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="4fe4c-111">Tercih edilen türleri okuma ya da kolayca yazılmış bir okuyucu veya yazan zinciri sonuna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="4fe4c-112">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="4fe4c-113">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir <xref:System.IO.StreamReader> karakterlerinden okumak için oluşturulan **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="4fe4c-114"><xref:System.IO.StreamReader.ReadLine%2A>kadar okur <xref:System.IO.StreamReader.Peek%2A> başka karakter bulur.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="4fe4c-115">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** varolan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="4fe4c-116">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir **BinaryReader** baytlar okumak için oluşturulan **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="4fe4c-117"><xref:System.IO.BinaryReader.ReadByte%2A>kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla baytı yok bulur.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4fe4c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
