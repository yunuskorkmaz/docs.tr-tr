---
title: 'Nasıl yapılır: dosyadan metin okuma'
description: Bu makalede, masaüstü uygulamaları için .NET 'teki StreamReader sınıfını kullanarak metin dosyasındaki metni zaman uyumlu veya zaman uyumsuz olarak okuma örneklerine bakın.
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
ms.openlocfilehash: cbdeab3e907b34b6658eef7228fa6567ae198b08
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447062"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="2464f-103">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="2464f-103">How to: Read text from a file</span></span>
<span data-ttu-id="2464f-104">Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2464f-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="2464f-105">Her iki örnekte, sınıfının örneğini oluşturduğunuzda <xref:System.IO.StreamReader> , dosyanın göreli veya mutlak yolunu sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="2464f-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2464f-106">Bu kod örnekleri, Evrensel Windows (UWP) uygulamaları için geliştirilmez, çünkü Windows Çalışma Zamanı dosyalara okuma ve yazma için farklı akış türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2464f-106">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="2464f-107">UWP uygulamasında bir dosyadaki metnin nasıl okunacağını gösteren bir örnek için bkz. [hızlı başlangıç: dosya okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="2464f-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="2464f-108">.NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında nasıl dönüştürme yapılacağını gösteren örnekler için bkz. [nasıl yapılır: .NET Framework akışlar ve Windows çalışma zamanı akışları arasında dönüştürme](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="2464f-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="2464f-109">Örnek: konsol uygulamasında zaman uyumlu okuma</span><span class="sxs-lookup"><span data-stu-id="2464f-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="2464f-110">Aşağıdaki örnek, bir konsol uygulaması içinde zaman uyumlu okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2464f-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="2464f-111">Bu örnek, bir akış okuyucusu kullanarak metin dosyasını açar, içeriği bir dizeye kopyalar ve dizeyi konsola verir.</span><span class="sxs-lookup"><span data-stu-id="2464f-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2464f-112">Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="2464f-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="2464f-113">Örnek: WPF uygulamasında zaman uyumsuz okuma</span><span class="sxs-lookup"><span data-stu-id="2464f-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="2464f-114">Aşağıdaki örnek, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2464f-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2464f-115">Örnek, *Testfile. txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="2464f-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2464f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2464f-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="2464f-117">Zaman uyumsuz dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="2464f-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="2464f-118">[Nasıl yapılır: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2464f-118">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="2464f-119">Hızlı başlangıç: dosyaları okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="2464f-119">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="2464f-120">Nasıl yapılır: .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2464f-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="2464f-121">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="2464f-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="2464f-122">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="2464f-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="2464f-123">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="2464f-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="2464f-124">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="2464f-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="2464f-125">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="2464f-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="2464f-126">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="2464f-126">File and stream I/O</span></span>](index.md)
