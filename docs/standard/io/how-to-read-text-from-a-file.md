---
title: 'Nasıl yapılır: dosyadan metin okuma'
ms.date: 01/03/2019
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
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155730"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="6b284-102">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="6b284-102">How to: Read text from a file</span></span>
<span data-ttu-id="6b284-103">Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b284-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="6b284-104">Her iki örnekte de, <xref:System.IO.StreamReader> sınıfının örneğini oluşturduğunuzda, dosyanın göreli veya mutlak yolunu sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="6b284-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6b284-105">Bu kod örnekleri, Evrensel Windows (UWP) uygulamaları için geliştirilmez, çünkü Windows Çalışma Zamanı dosyalara okuma ve yazma için farklı akış türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b284-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="6b284-106">UWP uygulamasında bir dosyadaki metnin nasıl okunacağını gösteren bir örnek için bkz. [hızlı başlangıç: dosya okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="6b284-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="6b284-107">.NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında nasıl dönüştürme yapılacağını gösteren örnekler için bkz. [nasıl yapılır: .NET Framework akışlar ve Windows çalışma zamanı akışları arasında dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="6b284-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="6b284-108">Örnek: konsol uygulamasında zaman uyumlu okuma</span><span class="sxs-lookup"><span data-stu-id="6b284-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="6b284-109">Aşağıdaki örnek, bir konsol uygulaması içinde zaman uyumlu okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b284-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="6b284-110">Bu örnek, bir akış okuyucusu kullanarak metin dosyasını açar, içeriği bir dizeye kopyalar ve dizeyi konsola verir.</span><span class="sxs-lookup"><span data-stu-id="6b284-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b284-111">Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6b284-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="6b284-112">Örnek: WPF uygulamasında zaman uyumsuz okuma</span><span class="sxs-lookup"><span data-stu-id="6b284-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="6b284-113">Aşağıdaki örnek, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b284-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b284-114">Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6b284-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6b284-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b284-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="6b284-116">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="6b284-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="6b284-117">[Nasıl yapılır: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b284-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="6b284-118">Hızlı başlangıç: dosyaları okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="6b284-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="6b284-119">Nasıl yapılır: .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6b284-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="6b284-120">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="6b284-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="6b284-121">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="6b284-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="6b284-122">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="6b284-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="6b284-123">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="6b284-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="6b284-124">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="6b284-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="6b284-125">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="6b284-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
