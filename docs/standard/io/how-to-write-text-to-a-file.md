---
title: 'Nasıl yapılır: Bir dosyaya metin yazma'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2fb5a30e165b78fef797bf8bfe536b66cae9a1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640758"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="e37f4-102">Nasıl yapılır: Bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="e37f4-102">How to: Write text to a file</span></span>
<span data-ttu-id="e37f4-103">Bu konu, bir .NET uygulaması için bir dosyaya metin yazma için farklı yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="e37f4-103">This topic shows different ways to write text to a file for a .NET app.</span></span> 

<span data-ttu-id="e37f4-104">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e37f4-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="e37f4-105"><xref:System.IO.StreamWriter> zaman uyumlu olarak bir dosyaya yazmak için yöntemleri içerir (<xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A>) veya zaman uyumsuz olarak (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="e37f4-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="e37f4-106"><xref:System.IO.File> metin gibi bir dosyaya yazmak için statik yöntemler sağlar <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>, veya gibi bir dosyaya metin eklenecek <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, ve <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="e37f4-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="e37f4-107"><xref:System.IO.Path> için dosya veya dizin yolu bilgileri olan strings olur.</span><span class="sxs-lookup"><span data-stu-id="e37f4-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="e37f4-108">İçerdiği <xref:System.IO.Path.Combine%2A> yöntemi ve .NET Core 2.1 ve sonraki sürümlerinde, <xref:System.IO.Path.Join%2A> ve <xref:System.IO.Path.TryJoin%2A> izin veren birleştirme dizelerin bir dosya veya dizin yolu oluşturmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e37f4-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="e37f4-109">Aşağıdaki örnekler yalnızca minimum gereken kod miktarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e37f4-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="e37f4-110">Gerçek uygulama genelde daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e37f4-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="e37f4-111">Örnek: Zaman uyumlu olarak StreamWriter ile metin yazma</span><span class="sxs-lookup"><span data-stu-id="e37f4-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="e37f4-112">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> zaman uyumlu olarak metin aynı anda yeni bir dosya bir satıra yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e37f4-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="e37f4-113">Çünkü <xref:System.IO.StreamWriter> nesne bildirildi ve içinde örneklenen bir `using` deyimi <xref:System.IO.StreamWriter.Dispose%2A> yöntemi çağrılır, otomatik olarak boşaltır ve akışı kapatır.</span><span class="sxs-lookup"><span data-stu-id="e37f4-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="e37f4-114">Örnek: Zaman uyumlu olarak StreamWriter ile metin ekleme</span><span class="sxs-lookup"><span data-stu-id="e37f4-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="e37f4-115">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> zaman uyumlu olarak metin ilk örnekte oluşturulan metin dosyasına eklenecek sınıf.</span><span class="sxs-lookup"><span data-stu-id="e37f4-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="e37f4-116">Örnek: Zaman uyumsuz olarak StreamWriter ile metin yazma</span><span class="sxs-lookup"><span data-stu-id="e37f4-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="e37f4-117">Aşağıdaki örnek, zaman uyumsuz olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e37f4-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="e37f4-118">Çağrılacak <xref:System.IO.StreamWriter.WriteAsync%2A> yöntem, yöntem çağrısının içinde olmalıdır bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e37f4-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="e37f4-119">C# Örnek gerektirir C# 7.1 veya sonraki sürümü için destek ekler `async` programın giriş noktası değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e37f4-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span> 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="e37f4-120">Örnek: Yazma ve metin dosyası sınıfı ekleme</span><span class="sxs-lookup"><span data-stu-id="e37f4-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="e37f4-121">Aşağıdaki örnek, yeni bir dosyaya metin yazma ve kullanarak aynı dosya için yeni satırlık metin ekleme işlemi gösterilmektedir <xref:System.IO.File> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e37f4-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="e37f4-122"><xref:System.IO.File.WriteAllText%2A> Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açın ve dosyayı otomatik olarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="e37f4-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="e37f4-123">Sağladığınız yolun, <xref:System.IO.File.WriteAllText%2A> yöntemi zaten var, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="e37f4-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="e37f4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e37f4-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e37f4-125">Nasıl yapılır: Dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e37f4-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="e37f4-126">Nasıl yapılır: İçin bir yeni oluşturulan veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="e37f4-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="e37f4-127">Nasıl yapılır: Açın ve bir günlük dosyasına Ekle</span><span class="sxs-lookup"><span data-stu-id="e37f4-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="e37f4-128">Nasıl yapılır: Bir dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="e37f4-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="e37f4-129">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="e37f4-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
