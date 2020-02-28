---
title: 'Nasıl yapılır: bir dosyaya metin yazma'
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160254"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="23e7a-102">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="23e7a-102">How to: Write text to a file</span></span>
<span data-ttu-id="23e7a-103">Bu konu başlığı altında, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yolları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="23e7a-104">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="23e7a-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="23e7a-105"><xref:System.IO.StreamWriter>, bir dosyaya (<xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A>) ya da zaman uyumsuz (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>) yazma yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="23e7a-106"><xref:System.IO.File>, <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>gibi bir dosyaya metin yazmak ya da <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>ve <xref:System.IO.File.AppendText%2A>gibi bir dosyaya metin eklemek için statik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="23e7a-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="23e7a-107"><xref:System.IO.Path>, dosya veya dizin yolu bilgilerine sahip dizeler içindir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="23e7a-108"><xref:System.IO.Path.Combine%2A> yöntemi ve .NET Core 2,1 ve üzeri sürümlerinde, dizelerin bitiştirilmesi için bir dosya veya dizin yolu oluşturma izni veren <xref:System.IO.Path.Join%2A> ve <xref:System.IO.Path.TryJoin%2A> yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="23e7a-109">Aşağıdaki örneklerde yalnızca gereken minimum kod miktarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="23e7a-110">Gerçek dünya uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="23e7a-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="23e7a-111">Örnek: StreamWriter ile eşzamanlı olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="23e7a-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="23e7a-112">Aşağıdaki örnek, bir kerede bir satırı yeni bir dosyaya zaman uyumlu olarak yazmak için <xref:System.IO.StreamWriter> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="23e7a-113"><xref:System.IO.StreamWriter> nesne `using` bildiriminde bildirildiği ve örneklendiği için, <xref:System.IO.StreamWriter.Dispose%2A> yöntemi çağrılır, bu da akışı otomatik olarak boşaltır ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="23e7a-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="23e7a-114">Örnek: bir StreamWriter ile eşzamanlı olarak metin ekleme</span><span class="sxs-lookup"><span data-stu-id="23e7a-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="23e7a-115">Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfının, ilk örnekte oluşturulan metin dosyasına zaman uyumlu olarak metin ekleme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="23e7a-116">Örnek: StreamWriter ile zaman uyumsuz olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="23e7a-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="23e7a-117">Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfını kullanarak nasıl zaman uyumsuz olarak yeni bir dosyaya metin yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="23e7a-118"><xref:System.IO.StreamWriter.WriteAsync%2A> yöntemini çağırmak için yöntem çağrısı bir `async` yöntemi içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23e7a-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="23e7a-119">C# Örnek, program C# giriş noktasındaki `async` değiştiricisi için destek ekleyen 7,1 veya sonraki bir sürümü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="23e7a-120">Örnek: dosya sınıfıyla metin yazın ve ekleyin</span><span class="sxs-lookup"><span data-stu-id="23e7a-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="23e7a-121">Aşağıdaki örnek, yeni bir dosyaya nasıl metin yazılacağını ve <xref:System.IO.File> sınıfını kullanarak aynı dosyaya yeni metin satırları ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23e7a-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="23e7a-122"><xref:System.IO.File.WriteAllText%2A> ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açıp dosyayı otomatik olarak kapatır.</span><span class="sxs-lookup"><span data-stu-id="23e7a-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="23e7a-123"><xref:System.IO.File.WriteAllText%2A> metoduna sağladığınız yol zaten varsa, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="23e7a-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="23e7a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23e7a-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="23e7a-125">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="23e7a-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="23e7a-126">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="23e7a-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="23e7a-127">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="23e7a-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="23e7a-128">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="23e7a-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="23e7a-129">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="23e7a-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
