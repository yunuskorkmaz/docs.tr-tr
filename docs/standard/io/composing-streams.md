---
description: 'Daha fazla bilgi edinin: oluşturma akışları'
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
ms.openlocfilehash: 55c3bd8b5f951397463d9f5c9c97efb6a1ef44b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782409"
---
# <a name="compose-streams"></a><span data-ttu-id="925f2-103">Akışları oluştur</span><span class="sxs-lookup"><span data-stu-id="925f2-103">Compose streams</span></span>

<span data-ttu-id="925f2-104">*Yedekleme deposu* , disk veya bellek gibi bir depolama ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="925f2-104">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="925f2-105">Her farklı yedekleme deposu, sınıfının bir uygulama olarak kendi akışını uygular <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="925f2-105">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="925f2-106">Her akış türü, ve ' den verilen yedekleme deposundan baytları okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="925f2-106">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="925f2-107">Yedekleme depolarına bağlanan akışlar *Temel akışlar* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="925f2-107">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="925f2-108">Temel akışlar, akışı yedekleme deposuna bağlamak için gereken parametrelere sahip oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="925f2-108">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="925f2-109">Örneğin, <xref:System.IO.FileStream> dosyanın işlemlerle nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturucular vardır.</span><span class="sxs-lookup"><span data-stu-id="925f2-109">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="925f2-110"><xref:System.IO>Sınıfların tasarımı Basitleştirilmiş akış kompozisyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="925f2-110">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="925f2-111">Temel akışları, istediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışlarına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="925f2-111">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="925f2-112">Zincirin sonuna bir okuyucu veya yazıcı ekleyebilirsiniz, böylece tercih edilen türler kolayca okunabilir veya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="925f2-112">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="925f2-113">Aşağıdaki kod örnekleri, *MyFile.txt* arabelleğe almak için mevcut *MyFile.txt* etrafında bir **FILESTREAM** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="925f2-113">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="925f2-114">**FileStreams** varsayılan olarak arabelleğe alınır ' i unutmayın.</span><span class="sxs-lookup"><span data-stu-id="925f2-114">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="925f2-115">Örnekler, *MyFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="925f2-115">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="925f2-116">Örnek: StreamReader kullanın</span><span class="sxs-lookup"><span data-stu-id="925f2-116">Example: Use StreamReader</span></span>

<span data-ttu-id="925f2-117">Aşağıdaki örnek, bir <xref:System.IO.StreamReader> ' ın Oluşturucu bağımsız değişkeni olarak **StreamReader** 'A geçirilmiş olan **FILESTREAM**'ten okuma karakterleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="925f2-117">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="925f2-118"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> ardından, <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> daha fazla karakter bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="925f2-118"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="925f2-119">Örnek: BinaryReader kullanın</span><span class="sxs-lookup"><span data-stu-id="925f2-119">Example: Use BinaryReader</span></span>

<span data-ttu-id="925f2-120">Aşağıdaki örnek, <xref:System.IO.BinaryReader> Oluşturucu bağımsız değişkeni olarak **BinaryReader** 'A geçirilmiş olan **FILESTREAM**'ten baytları okumak için bir, oluşturur.</span><span class="sxs-lookup"><span data-stu-id="925f2-120">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="925f2-121"><xref:System.IO.BinaryReader.ReadByte%2A> ardından, <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla bayt bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="925f2-121"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="925f2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="925f2-122">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
