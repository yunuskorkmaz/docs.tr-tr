---
title: 'Nasıl yapılır: Dosyadan Metin Okuma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e1058879d4af8aac12baf24d10a0c22894351e6f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="b5e0b-102">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-102">How to: Read Text from a File</span></span>
<span data-ttu-id="b5e0b-103">Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="b5e0b-104">Örneğini oluştururken hem örneklerde <xref:System.IO.StreamReader> sınıfı, dosya için göreli veya mutlak yol sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="b5e0b-105">Aşağıdaki örnek, uygulamayla aynı klasörde TestFile.txt adında bir dosya bulunduğunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="b5e0b-106">Windows Çalışma Zamanı, dosyalara okuma ve yazma için farklı akış türleri sağladığından, bu kod örnekleri Windows Mağazası uygulamaları için geliştirme uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-106">These code examples do not apply developing for Windows Store Apps because the Windows Runtime provides different streams types reading and writing to files.</span></span> <span data-ttu-id="b5e0b-107">Windows mağazası uygulaması bağlamında bir dosyadan metin okuma gösteren örnek için bkz: [hızlı başlangıç: Okuma ve dosyalara yazma](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx).</span><span class="sxs-lookup"><span data-stu-id="b5e0b-107">For an example that shows how to read text from a file within the context of a Windows Store app, see [Quickstart: Reading and writing files](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx).</span></span> <span data-ttu-id="b5e0b-108">.NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme gösteren örnekler için bkz [nasıl yapılır: .NET Framework akışları arasında dönüştürme ve Windows çalışma zamanı akışları](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="b5e0b-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5e0b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5e0b-109">Example</span></span>  
 <span data-ttu-id="b5e0b-110">İlk örnek bir konsol uygulamasında zaman uyumlu okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-110">The first example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="b5e0b-111">Bu örnekte, metin dosyası kullanarak bir akış okuyucusunu açıldığında, içeriği bir dizeye kopyalanır ve konsola çıktı dizedir.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-111">In this example, the text file is opened using a stream reader, the contents are copied to a string and string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b5e0b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5e0b-112">Example</span></span>  
 <span data-ttu-id="b5e0b-113">İkinci örnek bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-113">The second example shows an asynchronous read operation within a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b5e0b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5e0b-114">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b5e0b-115">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="b5e0b-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="b5e0b-116">NIB: Nasıl yapılır: bir dizin listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="b5e0b-117">Hızlı Başlangıç: Okuma ve dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-117">Quickstart: Reading and writing files</span></span>](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [<span data-ttu-id="b5e0b-118">Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b5e0b-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [<span data-ttu-id="b5e0b-119">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="b5e0b-120">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="b5e0b-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="b5e0b-121">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="b5e0b-122">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="b5e0b-123">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="b5e0b-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="b5e0b-124">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="b5e0b-124">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
