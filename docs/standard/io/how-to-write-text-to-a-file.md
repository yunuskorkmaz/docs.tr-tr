---
title: 'Nasıl yapılır: bir dosyaya metin yazma'
description: .NET uygulaması için bir dosyaya metin yazma veya ekleme yolları hakkında bilgi edinin. Metni zaman uyumlu veya zaman uyumsuz olarak yazmak için StreamWriter veya dosya sınıflarından yöntemler kullanın.
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
ms.openlocfilehash: 52d3d07f4ffdbdc6510425a65fc173d36e674d06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447218"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="6bcbc-104">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-104">How to: Write text to a file</span></span>
<span data-ttu-id="6bcbc-105">Bu konu başlığı altında, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yolları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-105">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="6bcbc-106">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6bcbc-106">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="6bcbc-107"><xref:System.IO.StreamWriter>bir dosyaya zaman uyumlu ( <xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A> ) veya zaman uyumsuz ( <xref:System.IO.StreamWriter.WriteAsync%2A> ve) yazma yöntemleri içerir <xref:System.IO.StreamWriter.WriteLineAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="6bcbc-107"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="6bcbc-108"><xref:System.IO.File>, ve gibi bir dosyaya metin yazmak için statik yöntemler sağlar; örneğin, <xref:System.IO.File.WriteAllLines%2A> <xref:System.IO.File.WriteAllText%2A> ve gibi bir dosyaya metin ekler <xref:System.IO.File.AppendAllLines%2A> <xref:System.IO.File.AppendAllText%2A> <xref:System.IO.File.AppendText%2A> .</span><span class="sxs-lookup"><span data-stu-id="6bcbc-108"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="6bcbc-109"><xref:System.IO.Path>dosya veya dizin yolu bilgilerine sahip dizeler içindir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-109"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="6bcbc-110">Bu yöntem, ve <xref:System.IO.Path.Combine%2A> .NET Core 2,1 ve sonraki sürümlerinde, <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> dizelerin bir dosya ya da dizin yolu oluşturmak için bitiştirilmesi sağlayan ve yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-110">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="6bcbc-111">Aşağıdaki örneklerde yalnızca gereken minimum kod miktarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-111">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="6bcbc-112">Gerçek dünya uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-112">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="6bcbc-113">Örnek: StreamWriter ile eşzamanlı olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-113">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="6bcbc-114">Aşağıdaki örnek, <xref:System.IO.StreamWriter> bir kerede bir satırı yeni bir dosyaya zaman uyumlu olarak yazmak için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-114">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="6bcbc-115"><xref:System.IO.StreamWriter>Nesne bir ifadede bildirildiği ve örneklendiği `using` için <xref:System.IO.StreamWriter.Dispose%2A> yöntem çağrılır, bu da akışı otomatik olarak boşaltır ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-115">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="6bcbc-116">Örnek: bir StreamWriter ile eşzamanlı olarak metin ekleme</span><span class="sxs-lookup"><span data-stu-id="6bcbc-116">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="6bcbc-117">Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfının, ilk örnekte oluşturulan metin dosyasına zaman uyumlu olarak metin ekleme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-117">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="6bcbc-118">Örnek: StreamWriter ile zaman uyumsuz olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-118">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="6bcbc-119">Aşağıdaki örnek, sınıfını kullanarak nasıl zaman uyumsuz olarak yeni bir dosyaya metin yazılacağını gösterir <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="6bcbc-119">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6bcbc-120">Yöntemi çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> Yöntem çağrısı bir yöntem içinde olmalıdır `async` .</span><span class="sxs-lookup"><span data-stu-id="6bcbc-120">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="6bcbc-121">C# örneği, `async` program giriş noktasındaki değiştirici için destek ekleyen c# 7,1 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-121">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="6bcbc-122">Örnek: dosya sınıfıyla metin yazın ve ekleyin</span><span class="sxs-lookup"><span data-stu-id="6bcbc-122">Example: Write and append text with the File class</span></span>

<span data-ttu-id="6bcbc-123">Aşağıdaki örnek, yeni bir dosyaya nasıl metin yazılacağını ve sınıfı kullanılarak aynı dosyaya yeni metin satırları ekleneceğini gösterir <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="6bcbc-123">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="6bcbc-124"><xref:System.IO.File.WriteAllText%2A>Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri, dosyayı otomatik olarak açar ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-124">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="6bcbc-125">Metoda sağladığınız yol <xref:System.IO.File.WriteAllText%2A> zaten varsa, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-125">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="6bcbc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bcbc-126">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6bcbc-127">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-127">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="6bcbc-128">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-128">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="6bcbc-129">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="6bcbc-129">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="6bcbc-130">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="6bcbc-130">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="6bcbc-131">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="6bcbc-131">File and stream I/O</span></span>](index.md)
