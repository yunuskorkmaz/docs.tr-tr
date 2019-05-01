---
title: 'Nasıl yapılır: Bir dizeye karakter yazma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947101"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="ae53f-102">Nasıl yapılır: Bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="ae53f-102">How to: Write characters to a string</span></span>
<span data-ttu-id="ae53f-103">Aşağıdaki kod örnekleri karakter zaman uyumlu veya zaman uyumsuz olarak bir karakter dizisinden bir dize olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="ae53f-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="ae53f-104">Örnek: Karakterleri bir konsol uygulamasında zaman uyumlu olarak yazma</span><span class="sxs-lookup"><span data-stu-id="ae53f-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="ae53f-105">Aşağıdaki örnekte bir <xref:System.IO.StringWriter> beş karakteri çok zaman uyumlu olarak yazmak için bir <xref:System.Text.StringBuilder> nesne.</span><span class="sxs-lookup"><span data-stu-id="ae53f-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span> 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="ae53f-106">Örnek: Karakterleri bir WPF uygulamasında zaman uyumsuz olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="ae53f-106">Example: Write characters asynchronously in a WPF app</span></span> 
 <span data-ttu-id="ae53f-107">Sonraki örnekte, bir WPF uygulaması arka plan kod bulunur.</span><span class="sxs-lookup"><span data-stu-id="ae53f-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="ae53f-108">Penceresi yüklendiğinde örnek zaman uyumsuz olarak tüm karakterleri okur. bir <xref:System.Windows.Controls.TextBox> denetleyebilir ve bunları bir dizide saklar.</span><span class="sxs-lookup"><span data-stu-id="ae53f-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="ae53f-109">Bunu sonra zaman uyumsuz olarak her bir harf veya boşluk karakteri ayrı bir satır yazan bir <xref:System.Windows.Controls.TextBlock> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ae53f-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae53f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae53f-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="ae53f-111">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="ae53f-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="ae53f-112">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="ae53f-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="ae53f-113">Nasıl yapılır: Dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="ae53f-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="ae53f-114">Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="ae53f-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="ae53f-115">Nasıl yapılır: Açın ve bir günlük dosyasına Ekle</span><span class="sxs-lookup"><span data-stu-id="ae53f-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="ae53f-116">Nasıl yapılır: Bir dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="ae53f-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="ae53f-117">Nasıl yapılır: Bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="ae53f-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="ae53f-118">Nasıl yapılır: Dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="ae53f-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
