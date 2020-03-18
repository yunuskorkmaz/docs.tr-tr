---
title: 'Nasıl yapilir: Bir dizedeki karakterleri okuma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155769"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="d3b76-102">Nasıl yapilir: Bir dizedeki karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="d3b76-102">How to: Read characters from a string</span></span>
<span data-ttu-id="d3b76-103">Aşağıdaki kod örnekleri, karakterlerin eşzamanlı olarak veya bir dizeden eşzamanlı olarak nasıl okunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3b76-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="d3b76-104">Örnek: Karakterleri eşzamanlı olarak okuyun</span><span class="sxs-lookup"><span data-stu-id="d3b76-104">Example: Read characters synchronously</span></span>
 <span data-ttu-id="d3b76-105">Bu örnek, bir dizeden eşzamanlı olarak 13 karakter okur, bunları bir dizide saklar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d3b76-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="d3b76-106">Örnek daha sonra dizedeki karakterlerin geri kalanını okur, altıncı öğeden başlayarak dizide saklar ve dizinin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d3b76-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="d3b76-107">Örnek: Karakterleri eşzamanlı olarak okuyun</span><span class="sxs-lookup"><span data-stu-id="d3b76-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="d3b76-108">Sonraki örnek, bir WPF uygulamasının arkasındaki koddur.</span><span class="sxs-lookup"><span data-stu-id="d3b76-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="d3b76-109">Pencere yükünde, örnek tüm karakterleri denetimden <xref:System.Windows.Controls.TextBox> eşit bir şekilde okur ve bir dizide saklar.</span><span class="sxs-lookup"><span data-stu-id="d3b76-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="d3b76-110">Daha sonra eşzamanlı bir denetim ayrı bir satıra <xref:System.Windows.Controls.TextBlock> her harf veya beyaz boşluk karakter yazar.</span><span class="sxs-lookup"><span data-stu-id="d3b76-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3b76-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b76-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d3b76-112">Asynchronous dosya I/O</span><span class="sxs-lookup"><span data-stu-id="d3b76-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="d3b76-113">[Nasıl yapılsın: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3b76-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="d3b76-114">Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="d3b76-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="d3b76-115">Nasıl yapılı: Günlük dosyasını açma ve ekle</span><span class="sxs-lookup"><span data-stu-id="d3b76-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="d3b76-116">Nasıl yapilir: Dosyadaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="d3b76-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="d3b76-117">Nasıl yazılır: Dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="d3b76-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="d3b76-118">Nasıl yazılır: Karakterleri bir dize yazma</span><span class="sxs-lookup"><span data-stu-id="d3b76-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="d3b76-119">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="d3b76-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
