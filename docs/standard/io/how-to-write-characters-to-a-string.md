---
title: 'Nasıl yapılır: bir dizeye karakter yazma'
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: d4a6bbc77a9feb16293fc88e1598d124d8d2d75d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829732"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="da624-102">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="da624-102">How to: Write characters to a string</span></span>

<span data-ttu-id="da624-103">Aşağıdaki kod örnekleri, bir karakter dizisinden dize içine zaman uyumlu veya zaman uyumsuz karakterler yazar.</span><span class="sxs-lookup"><span data-stu-id="da624-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="da624-104">Örnek: bir konsol uygulamasında karakterleri eşzamanlı olarak yazma</span><span class="sxs-lookup"><span data-stu-id="da624-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="da624-105">Aşağıdaki örnek, bir <xref:System.IO.StringWriter> nesnesine beş karakter eşzamanlı yazmak için bir kullanır <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="da624-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="da624-106">Örnek: bir WPF uygulamasında karakterleri zaman uyumsuz olarak yazma</span><span class="sxs-lookup"><span data-stu-id="da624-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="da624-107">Sonraki örnek, bir WPF uygulamasının arkasındaki koddur.</span><span class="sxs-lookup"><span data-stu-id="da624-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="da624-108">Pencere yükleme sırasında örnek, bir denetimdeki tüm karakterleri zaman uyumsuz olarak okur <xref:System.Windows.Controls.TextBox> ve bunları bir dizide depolar.</span><span class="sxs-lookup"><span data-stu-id="da624-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="da624-109">Ardından, her bir harfi veya boşluk karakterini bir denetimin ayrı bir satırına zaman uyumsuz olarak yazar <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="da624-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="da624-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da624-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="da624-111">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="da624-111">File and stream I/O</span></span>](index.md)  
- [<span data-ttu-id="da624-112">Zaman uyumsuz dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="da624-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- [<span data-ttu-id="da624-113">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="da624-113">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="da624-114">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="da624-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="da624-115">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="da624-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="da624-116">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="da624-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="da624-117">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="da624-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="da624-118">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="da624-118">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)
