---
title: Zaman Uyumsuz Dosya G/Ç
description: .NET 'teki zaman uyumsuz dosya g/ç hakkında bilgi edinin. ReadAsync, WriteAsync ve daha fazlası gibi zaman uyumsuz işlemleri basitleştirecek zaman uyumsuz yöntemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: a148e6e13ec0ee4ee469a0630f150199c5a3af13
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188607"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="4a61c-104">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="4a61c-104">Asynchronous File I/O</span></span>

<span data-ttu-id="4a61c-105">Zaman uyumsuz işlemler, yoğun kaynak kullanan I/O işlemlerini ana iş parçacığını engellemeden gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a61c-105">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="4a61c-106">Bu performans açısından, zaman alan bir akış işleminin Kullanıcı arabirimi iş parçacığını engelleyebileceği ve uygulamanızın çalışmıyor gibi görünmesine neden olduğu bir Windows 8. x Mağazası uygulamasında veya masaüstü uygulamasında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4a61c-106">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="4a61c-107">.NET Framework 4,5 ' den başlayarak, g/ç türleri zaman uyumsuz işlemleri basitleştirecek zaman uyumsuz yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4a61c-107">Starting with .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="4a61c-108">Bir zaman uyumsuz yöntem, adında `Async` içerir; örneğin <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> ve <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a61c-108">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="4a61c-109">Bu zaman uyumsuz yöntemler, <xref:System.IO.Stream>, <xref:System.IO.FileStream> ve <xref:System.IO.MemoryStream> gibi akış sınıflarında ve <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> gibi akışlarda okuma ve yazma işlemi yapan sınıflarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a61c-109">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="4a61c-110">.NET Framework 4 ve önceki sürümlerde, <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> zaman uyumsuz g/ç işlemlerini uygulamak için ve gibi yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a61c-110">In .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="4a61c-111">Bu yöntemler, eski kodu desteklemek için geçerli .NET sürümlerinde hala kullanılabilir; Ancak zaman uyumsuz yöntemler, zaman uyumsuz g/ç işlemlerini daha kolay uygulamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4a61c-111">These methods are still available in current .NET versions to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="4a61c-112">C# ve Visual Basic, zaman uyumsuz programlama için iki anahtar sözcüğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4a61c-112">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="4a61c-113">Zaman uyumsuz bir işlem içeren bir yöntemi işaretlemek için kullanılan `Async` (Visual Basic) veya `async` (C#) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4a61c-113">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="4a61c-114">Bir zaman uyumsuz yöntemin sonucuna uygulanan `Await` (Visual Basic) veya `await` (C#) işleci.</span><span class="sxs-lookup"><span data-stu-id="4a61c-114">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="4a61c-115">Zaman uyumsuz G/Ç işlemlerini uygulamak için, aşağıdaki örneklerde gösterildiği üzere zaman uyumsuz yöntemlerle bu anahtar sözcükleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a61c-115">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="4a61c-116">Daha fazla bilgi için bkz. [Async ve await (C#) ile](../../csharp/programming-guide/concepts/async/index.md) zaman uyumsuz programlama veya [Async ve await Ile zaman uyumsuz programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a61c-116">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="4a61c-117">Aşağıdaki örnek, dosyaları zaman uyumsuz olarak bir dizinden başka bir dizine kopyalamak için <xref:System.IO.FileStream> nesnelerini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a61c-117">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="4a61c-118"><xref:System.Web.UI.WebControls.Button.Click> denetimi için <xref:System.Windows.Controls.Button> olay işleyicisinin, zaman uyumsuz bir yöntem çağırdığı için `async` değiştiricisi ile işaretlendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4a61c-118">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="4a61c-119">Sonraki örnek öncekine benzer, ancak bir metin dosyasının içeriğini zaman uyumsuz olarak okumak için <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> nesnelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a61c-119">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="4a61c-120">Sonraki örnekte, bir dosyayı bir Windows 8. x Mağazası uygulamasında bir dosya olarak açmak için kullanılan arka plan kod dosyası ve XAML dosyası ve <xref:System.IO.Stream> sınıfının bir örneğini kullanarak içeriğini okumak gösterilmektedir <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="4a61c-120">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="4a61c-121">Dosyayı bir akış olarak açmak ve içeriğini okumak için zaman uyumsuz yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a61c-121">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="4a61c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a61c-122">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="4a61c-123">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="4a61c-123">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="4a61c-124">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="4a61c-124">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4a61c-125">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a61c-125">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
