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
ms.openlocfilehash: 395344accf5be416fbcc527e51ba83408f9c5810
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291740"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="32017-102">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="32017-102">How to: Write text to a file</span></span>
<span data-ttu-id="32017-103">Bu konu başlığı altında, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yolları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32017-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="32017-104">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="32017-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="32017-105"><xref:System.IO.StreamWriter>bir dosyaya zaman uyumlu ( <xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A> ) veya zaman uyumsuz ( <xref:System.IO.StreamWriter.WriteAsync%2A> ve) yazma yöntemleri içerir <xref:System.IO.StreamWriter.WriteLineAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="32017-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="32017-106"><xref:System.IO.File>, ve gibi bir dosyaya metin yazmak için statik yöntemler sağlar; örneğin, <xref:System.IO.File.WriteAllLines%2A> <xref:System.IO.File.WriteAllText%2A> ve gibi bir dosyaya metin ekler <xref:System.IO.File.AppendAllLines%2A> <xref:System.IO.File.AppendAllText%2A> <xref:System.IO.File.AppendText%2A> .</span><span class="sxs-lookup"><span data-stu-id="32017-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="32017-107"><xref:System.IO.Path>dosya veya dizin yolu bilgilerine sahip dizeler içindir.</span><span class="sxs-lookup"><span data-stu-id="32017-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="32017-108">Bu yöntem, ve <xref:System.IO.Path.Combine%2A> .NET Core 2,1 ve sonraki sürümlerinde, <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> dizelerin bir dosya ya da dizin yolu oluşturmak için bitiştirilmesi sağlayan ve yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="32017-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="32017-109">Aşağıdaki örneklerde yalnızca gereken minimum kod miktarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32017-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="32017-110">Gerçek dünya uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="32017-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="32017-111">Örnek: StreamWriter ile eşzamanlı olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="32017-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="32017-112">Aşağıdaki örnek, <xref:System.IO.StreamWriter> bir kerede bir satırı yeni bir dosyaya zaman uyumlu olarak yazmak için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="32017-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="32017-113"><xref:System.IO.StreamWriter>Nesne bir ifadede bildirildiği ve örneklendiği `using` için <xref:System.IO.StreamWriter.Dispose%2A> yöntem çağrılır, bu da akışı otomatik olarak boşaltır ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="32017-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="32017-114">Örnek: bir StreamWriter ile eşzamanlı olarak metin ekleme</span><span class="sxs-lookup"><span data-stu-id="32017-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="32017-115">Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfının, ilk örnekte oluşturulan metin dosyasına zaman uyumlu olarak metin ekleme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32017-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="32017-116">Örnek: StreamWriter ile zaman uyumsuz olarak metin yazma</span><span class="sxs-lookup"><span data-stu-id="32017-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="32017-117">Aşağıdaki örnek, sınıfını kullanarak nasıl zaman uyumsuz olarak yeni bir dosyaya metin yazılacağını gösterir <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="32017-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="32017-118">Yöntemi çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> Yöntem çağrısı bir yöntem içinde olmalıdır `async` .</span><span class="sxs-lookup"><span data-stu-id="32017-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="32017-119">C# örneği, `async` program giriş noktasındaki değiştirici için destek ekleyen c# 7,1 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32017-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="32017-120">Örnek: dosya sınıfıyla metin yazın ve ekleyin</span><span class="sxs-lookup"><span data-stu-id="32017-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="32017-121">Aşağıdaki örnek, yeni bir dosyaya nasıl metin yazılacağını ve sınıfı kullanılarak aynı dosyaya yeni metin satırları ekleneceğini gösterir <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="32017-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="32017-122"><xref:System.IO.File.WriteAllText%2A>Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri, dosyayı otomatik olarak açar ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="32017-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="32017-123">Metoda sağladığınız yol <xref:System.IO.File.WriteAllText%2A> zaten varsa, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="32017-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="32017-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32017-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="32017-125">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="32017-125">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="32017-126">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="32017-126">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="32017-127">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="32017-127">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="32017-128">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="32017-128">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="32017-129">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="32017-129">File and stream I/O</span></span>](index.md)
