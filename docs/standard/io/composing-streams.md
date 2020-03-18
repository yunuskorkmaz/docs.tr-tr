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
# <a name="compose-streams"></a><span data-ttu-id="102f3-102">Akışlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="102f3-102">Compose streams</span></span>
<span data-ttu-id="102f3-103">*Destek deposu,* disk veya bellek gibi bir depolama ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="102f3-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="102f3-104">Her farklı destek deposu <xref:System.IO.Stream> sınıfın bir uygulaması olarak kendi akışını uygular.</span><span class="sxs-lookup"><span data-stu-id="102f3-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="102f3-105">Her akış türü, verilen destek deposundan baytları okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="102f3-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="102f3-106">Destek depolarına bağlanan akışlara *temel akış*denir.</span><span class="sxs-lookup"><span data-stu-id="102f3-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="102f3-107">Temel akışlarda, akışı destek deposuna bağlamak için gerekli parametrelere sahip yapıcılar vardır.</span><span class="sxs-lookup"><span data-stu-id="102f3-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="102f3-108">Örneğin, <xref:System.IO.FileStream> dosyanın işlemler tarafından nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturucular vardır.</span><span class="sxs-lookup"><span data-stu-id="102f3-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="102f3-109"><xref:System.IO> Sınıfların tasarımı basitleştirilmiş akış kompozisyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="102f3-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="102f3-110">İstediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışına temel akışlar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="102f3-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="102f3-111">Tercih edilen türleri kolayca okunabilir veya yazılabilir, böylece zincirin sonuna bir okuyucu veya yazar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="102f3-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="102f3-112">Aşağıdaki kod örnekleri *MyFile.txt'yi*arabelleğe almak için varolan *MyFile.txt'nin* etrafında bir **FileStream** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="102f3-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="102f3-113">**FileStreams** varsayılan olarak arabelleğe olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="102f3-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="102f3-114">Örnekler, *MyFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten mevcut olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="102f3-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="102f3-115">Örnek: StreamReader'ı kullanın</span><span class="sxs-lookup"><span data-stu-id="102f3-115">Example: Use StreamReader</span></span>
<span data-ttu-id="102f3-116">Aşağıdaki örnek, oluşturan <xref:System.IO.StreamReader> bağımsız değişken olarak **StreamReader'a** geçirilen **FileStream'den**okunacak karakterler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="102f3-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="102f3-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>sonra başka <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> karakter bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="102f3-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="102f3-118">Örnek: BinaryReader kullanın</span><span class="sxs-lookup"><span data-stu-id="102f3-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="102f3-119">Aşağıdaki örnek, kurucu <xref:System.IO.BinaryReader> bağımsız değişkeni olarak **BinaryReader'a** geçirilen **FileStream'den**okunacak baytlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="102f3-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="102f3-120"><xref:System.IO.BinaryReader.ReadByte%2A>sonra daha <xref:System.IO.BinaryReader.PeekChar%2A> fazla bayt bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="102f3-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="102f3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="102f3-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
