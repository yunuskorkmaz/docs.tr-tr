---
title: 'Nasıl yapılır: Dosyadan Metin Okuma'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7c54e5e55770f3df44819cdf6d2d2c866f7e0fc
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298168"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="0723c-102">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="0723c-102">How to: Read Text from a File</span></span>
<span data-ttu-id="0723c-103">Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0723c-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="0723c-104">Örneğini oluştururken hem örneklerde <xref:System.IO.StreamReader> sınıfı, dosya için göreli veya mutlak yol sağlayın.</span><span class="sxs-lookup"><span data-stu-id="0723c-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="0723c-105">Aşağıdaki örnek, uygulamayla aynı klasörde TestFile.txt adında bir dosya bulunduğunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0723c-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="0723c-106">Bu kod örnekleri Windows çalışma zamanı dosyaları için okuma ve yazma için farklı akış türleri sağladığından için Windows mağazası uygulamaları geliştirmek için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="0723c-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="0723c-107">Bir Windows mağazası uygulamasında bir dosyadan metin okuma gösteren örnek için bkz: [hızlı başlangıç: Okuma ve dosyalara yazma](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="0723c-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="0723c-108">.NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme Göster örnekler için bkz: [nasıl yapılır: .NET Framework akışları arasında dönüştürme ve Windows çalışma zamanı akışları](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="0723c-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0723c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0723c-109">Example</span></span>  
 <span data-ttu-id="0723c-110">Aşağıdaki örnek bir konsol uygulaması içinde eşzamanlı okuma işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0723c-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="0723c-111">Bu örnekte, metin dosyası kullanarak bir akış okuyucusunu açıldığında, içeriği bir dizeye kopyalanır ve konsola çıktı dizedir.</span><span class="sxs-lookup"><span data-stu-id="0723c-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0723c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0723c-112">Example</span></span>  
 <span data-ttu-id="0723c-113">Aşağıdaki örnekte, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0723c-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0723c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0723c-114">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0723c-115">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="0723c-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="0723c-116">NIB: Nasıl yapılır: bir dizin listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0723c-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="0723c-117">Hızlı Başlangıç: Okuma ve dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="0723c-117">Quickstart: Reading and writing files</span></span>](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [<span data-ttu-id="0723c-118">Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0723c-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [<span data-ttu-id="0723c-119">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="0723c-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="0723c-120">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="0723c-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="0723c-121">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="0723c-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="0723c-122">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="0723c-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="0723c-123">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="0723c-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="0723c-124">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="0723c-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
