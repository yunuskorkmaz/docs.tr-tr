---
title: Akışlar Oluşturma
ms.date: 03/30/2017
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
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509399"
---
# <a name="composing-streams"></a><span data-ttu-id="23b7f-102">Akışlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="23b7f-102">Composing Streams</span></span>
<span data-ttu-id="23b7f-103">Bir disk veya bellek gibi bir depolama ortamına bir yedekleme deposudur.</span><span class="sxs-lookup"><span data-stu-id="23b7f-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="23b7f-104">Her farklı yedekleme deposu uygulaması kendi akış uygulayan <xref:System.IO.Stream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="23b7f-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="23b7f-105">Her akış türü okur ve Kimden ve Kime, belirtilen yedekleme deposu bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="23b7f-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="23b7f-106">Temel akışlar depoları için bağlandığı akışları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="23b7f-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="23b7f-107">Temel akışlar yedekleme deposu için akışa bağlanmak için gereken parametrelerine sahip oluşturucular sahiptir.</span><span class="sxs-lookup"><span data-stu-id="23b7f-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="23b7f-108">Örneğin, <xref:System.IO.FileStream> dosya işlemleri ve benzeri nasıl paylaşılır belirtir bir yol parametresi belirtin Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="23b7f-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="23b7f-109">Tasarımını <xref:System.IO> sınıflar, Basitleştirilmiş akış oluşturmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="23b7f-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="23b7f-110">Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23b7f-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="23b7f-111">Tercih edilen türleri okuma ya da kolayca yazılan okuyucuya veya yazara zinciri sonuna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23b7f-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="23b7f-112">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** var olan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="23b7f-113">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir <xref:System.IO.StreamReader> karakterleri okumak için oluşturulan **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="23b7f-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="23b7f-114"><xref:System.IO.StreamReader.ReadLine%2A> kadar okur <xref:System.IO.StreamReader.Peek%2A> başka karakter bulur.</span><span class="sxs-lookup"><span data-stu-id="23b7f-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="23b7f-115">Aşağıdaki kod örneği oluşturur bir **FILESTREAM** var olan geçici `MyFile.txt` arabellek sırada `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="23b7f-116">(Unutmayın **FileStreams** varsayılan olarak arabelleğe.) Ardından, bir **BinaryReader** bayt okumak için oluşturulan **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="23b7f-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="23b7f-117"><xref:System.IO.BinaryReader.ReadByte%2A> kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> hiçbir daha fazla bayt bulur.</span><span class="sxs-lookup"><span data-stu-id="23b7f-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="23b7f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23b7f-118">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
