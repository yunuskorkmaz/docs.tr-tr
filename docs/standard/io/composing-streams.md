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
ms.openlocfilehash: 3f18712793254f4942c092c87a3e64c73b492ae0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160111"
---
# <a name="compose-streams"></a><span data-ttu-id="d1b92-102">Akışları oluştur</span><span class="sxs-lookup"><span data-stu-id="d1b92-102">Compose streams</span></span>
<span data-ttu-id="d1b92-103">*Yedekleme deposu* , disk veya bellek gibi bir depolama ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="d1b92-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="d1b92-104">Her farklı yedekleme deposu, <xref:System.IO.Stream> sınıfının bir uygulama olarak kendi akışını uygular.</span><span class="sxs-lookup"><span data-stu-id="d1b92-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="d1b92-105">Her akış türü, ve ' den verilen yedekleme deposundan baytları okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="d1b92-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="d1b92-106">Yedekleme depolarına bağlanan akışlar *Temel akışlar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d1b92-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="d1b92-107">Temel akışlar, akışı yedekleme deposuna bağlamak için gereken parametrelere sahip oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="d1b92-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="d1b92-108">Örneğin, <xref:System.IO.FileStream>, dosyanın işlemlerle nasıl paylaşılacağını belirten bir yol parametresi belirten oluşturuculara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d1b92-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="d1b92-109"><xref:System.IO> sınıflarının tasarımı Basitleştirilmiş akış oluşturmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1b92-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="d1b92-110">Temel akışları, istediğiniz işlevselliği sağlayan bir veya daha fazla geçiş akışlarına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1b92-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="d1b92-111">Zincirin sonuna bir okuyucu veya yazıcı ekleyebilirsiniz, böylece tercih edilen türler kolayca okunabilir veya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1b92-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="d1b92-112">Aşağıdaki kod örnekleri, *Dosyam. txt*' i arabelleğe almak Için mevcut *Dosyam. txt* etrafında bir **FILESTREAM** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1b92-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="d1b92-113">**FileStreams** varsayılan olarak arabelleğe alınır ' i unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d1b92-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d1b92-114">Örneklerde, *Dosyam. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten varolduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d1b92-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="d1b92-115">Örnek: StreamReader kullanın</span><span class="sxs-lookup"><span data-stu-id="d1b92-115">Example: Use StreamReader</span></span>
<span data-ttu-id="d1b92-116">Aşağıdaki örnek, bir ' ın Oluşturucu bağımsız değişkeni olarak **StreamReader** 'a geçirildiği, **FILESTREAM**'ten karakter okumak için bir <xref:System.IO.StreamReader> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1b92-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="d1b92-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>, <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> daha fazla karakter bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="d1b92-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="d1b92-118">Örnek: BinaryReader kullanın</span><span class="sxs-lookup"><span data-stu-id="d1b92-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="d1b92-119">Aşağıdaki örnek, Oluşturucu bağımsız değişkeni olarak **BinaryReader** 'a geçirilen, **FILESTREAM**'ten bayt okumak için bir <xref:System.IO.BinaryReader> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1b92-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="d1b92-120"><xref:System.IO.BinaryReader.ReadByte%2A>, <xref:System.IO.BinaryReader.PeekChar%2A> daha fazla bayt bulana kadar okur.</span><span class="sxs-lookup"><span data-stu-id="d1b92-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d1b92-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1b92-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
