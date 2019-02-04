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
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674353"
---
# <a name="compose-streams"></a><span data-ttu-id="fe4cd-102">Akışlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe4cd-102">Compose streams</span></span>
<span data-ttu-id="fe4cd-103">A *yedekleme deposu* disk veya bellek gibi bir depolama Orta'dır.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="fe4cd-104">Her farklı yedekleme deposu uygulaması kendi akış uygulayan <xref:System.IO.Stream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> 

<span data-ttu-id="fe4cd-105">Her akış türü okur ve Kimden ve Kime, belirtilen yedekleme deposu bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="fe4cd-106">Depoları için bağlandığı akışları çağrılır *temel akışları*.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="fe4cd-107">Temel akışlar yedekleme deposu için akışa bağlanmak için gereken parametreleri oluşturucularla vardır.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="fe4cd-108">Örneğin, <xref:System.IO.FileStream> dosya işlemler tarafından nasıl paylaşılır belirtir bir yol parametresi belirtin Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="fe4cd-109">Tasarımını <xref:System.IO> basitleştirilmiş bir akış oluşturma sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="fe4cd-110">Temel akışlar istediğiniz işlevleri sağlayan bir veya daha fazla geçiş akışlara ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="fe4cd-111">Tercih edilen türleri okuma ya da kolayca yazılan okuyucuya veya yazara zinciri sonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="fe4cd-112">Aşağıdaki kod örnekleri oluşturma bir **FILESTREAM** var olan geçici *MyFile.txt* arabellek sırada *MyFile.txt*.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="fe4cd-113">Unutmayın **FileStreams** varsayılan olarak ara belleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="fe4cd-114">Örnekler adlı bir dosya olduğunu varsayar *MyFile.txt* uygulama ile aynı klasörde zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="fe4cd-115">Örnek: StreamReader kullanın</span><span class="sxs-lookup"><span data-stu-id="fe4cd-115">Example: Use StreamReader</span></span>
<span data-ttu-id="fe4cd-116">Aşağıdaki örnek, oluşturur bir <xref:System.IO.StreamReader> karakterleri okumak için **FILESTREAM**, için geçirilen **StreamReader** oluşturucu bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="fe4cd-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> Daha sonra kadar okur <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> başka karakter bulur.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="fe4cd-118">Örnek: BinaryReader kullanın</span><span class="sxs-lookup"><span data-stu-id="fe4cd-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="fe4cd-119">Aşağıdaki örnek, oluşturur bir <xref:System.IO.BinaryReader> bayt okunacak **FILESTREAM**, için geçirilen **BinaryReader** oluşturucu bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="fe4cd-120"><xref:System.IO.BinaryReader.ReadByte%2A> Daha sonra kadar okur <xref:System.IO.BinaryReader.PeekChar%2A> hiçbir daha fazla bayt bulur.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="fe4cd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4cd-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
