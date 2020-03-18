---
title: 'Nasıl yazılır: Dosyaya metin yazma'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160254"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="6e54b-102">Nasıl yazılır: Dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="6e54b-102">How to: Write text to a file</span></span>
<span data-ttu-id="6e54b-103">Bu konu, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="6e54b-104">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6e54b-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="6e54b-105"><xref:System.IO.StreamWriter>bir dosyaya eşzamanlı olarak<xref:System.IO.StreamWriter.Write%2A> (ve) <xref:System.IO.TextWriter.WriteLine%2A>veya eşzamanlı olarak<xref:System.IO.StreamWriter.WriteAsync%2A> (ve) <xref:System.IO.StreamWriter.WriteLineAsync%2A>yazma yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="6e54b-106"><xref:System.IO.File>gibi bir dosyaya metin yazmak <xref:System.IO.File.WriteAllLines%2A> için <xref:System.IO.File.WriteAllText%2A>statik yöntemler sağlar ve , veya <xref:System.IO.File.AppendAllLines%2A>bir <xref:System.IO.File.AppendAllText%2A>dosyaya metin eklemek için , , ve <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e54b-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="6e54b-107"><xref:System.IO.Path>dosya veya dizin yolu bilgilerine sahip dizeleri içindir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="6e54b-108">Bir dosya <xref:System.IO.Path.Combine%2A> veya dizin yolu oluşturmak için dizeleri <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> biraraya getiren yöntem ve .NET Core 2.1 ve daha sonra, ve daha sonra, ve yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="6e54b-109">Aşağıdaki örnekler, yalnızca gereken minimum kod miktarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="6e54b-110">Gerçek bir uygulama genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e54b-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="6e54b-111">Örnek: StreamWriter ile eşzamanlı metin yazma</span><span class="sxs-lookup"><span data-stu-id="6e54b-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="6e54b-112">Aşağıdaki örnek, bir seferde <xref:System.IO.StreamWriter> yeni bir dosyaya eşit olarak metin yazmak için sınıfın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="6e54b-113"><xref:System.IO.StreamWriter> Nesne bir `using` deyimde beyan edilip anında çağrıldığı için, <xref:System.IO.StreamWriter.Dispose%2A> yöntem çağrılır ve bu yöntem akışı otomatik olarak temizler ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="6e54b-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="6e54b-114">Örnek: StreamWriter ile eşzamanlı olarak metin ekle</span><span class="sxs-lookup"><span data-stu-id="6e54b-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="6e54b-115">Aşağıdaki örnekte, ilk <xref:System.IO.StreamWriter> örnekte oluşturulan metin dosyasına eşit olarak metin eklemek için sınıfın nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="6e54b-116">Örnek: StreamWriter ile eşzamanlı metin yazmak</span><span class="sxs-lookup"><span data-stu-id="6e54b-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="6e54b-117">Aşağıdaki örnek, sınıfı kullanarak yeni bir dosyaya eş <xref:System.IO.StreamWriter> senkronize metin yazmanın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6e54b-118"><xref:System.IO.StreamWriter.WriteAsync%2A> Yöntemi çağırmak için yöntem çağrısının bir `async` yöntem içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="6e54b-119">C# örneği C# 7.1 veya daha sonra `async` gerektirir, bu da program giriş noktasındaki değiştirici için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="6e54b-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="6e54b-120">Örnek: Dosya sınıfıyla metin yazma ve ekle</span><span class="sxs-lookup"><span data-stu-id="6e54b-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="6e54b-121">Aşağıdaki örnek, yeni bir dosyaya metin yazmanın ve sınıfı kullanarak aynı <xref:System.IO.File> dosyaya yeni metin satırlarının nasıl eklenilen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e54b-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="6e54b-122">Ve <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> yöntemleri dosyayı otomatik olarak açıp kapatır.</span><span class="sxs-lookup"><span data-stu-id="6e54b-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="6e54b-123"><xref:System.IO.File.WriteAllText%2A> Yönteme sağladığınız yol zaten varsa, dosya üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="6e54b-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="6e54b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e54b-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6e54b-125">Nasıl yapılır: Dizinleri ve dosyaları sayısal</span><span class="sxs-lookup"><span data-stu-id="6e54b-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="6e54b-126">Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="6e54b-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="6e54b-127">Nasıl yapılı: Günlük dosyasını açma ve ekle</span><span class="sxs-lookup"><span data-stu-id="6e54b-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="6e54b-128">Nasıl yapilir: Dosyadaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="6e54b-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="6e54b-129">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="6e54b-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
