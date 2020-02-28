---
title: 'Nasıl yapılır: dizeden karakterleri okuma'
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155769"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="0ba3b-102">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="0ba3b-102">How to: Read characters from a string</span></span>
<span data-ttu-id="0ba3b-103">Aşağıdaki kod örnekleri, bir dizeden zaman uyumlu veya zaman uyumsuz karakterlerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="0ba3b-104">Örnek: karakterleri zaman uyumlu olarak okuyun</span><span class="sxs-lookup"><span data-stu-id="0ba3b-104">Example: Read characters synchronously</span></span>
 <span data-ttu-id="0ba3b-105">Bu örnek, bir dizeden zaman uyumlu olarak 13 karakter okur, bunları bir dizide depolar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="0ba3b-106">Örnek daha sonra dizedeki karakterlerin geri kalanını okur, bunları altıncı öğeden başlayarak dizide depolar ve dizinin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="0ba3b-107">Örnek: karakterleri zaman uyumsuz olarak oku</span><span class="sxs-lookup"><span data-stu-id="0ba3b-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="0ba3b-108">Sonraki örnek, bir WPF uygulamasının arkasındaki koddur.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="0ba3b-109">Pencere yükleme sırasında, örnek zaman uyumsuz olarak bir <xref:System.Windows.Controls.TextBox> denetimindeki tüm karakterleri okur ve bunları bir dizide depolar.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="0ba3b-110">Ardından, her bir harfi veya boşluk karakterini <xref:System.Windows.Controls.TextBlock> denetimin ayrı bir satırına zaman uyumsuz olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0ba3b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba3b-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="0ba3b-112">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="0ba3b-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="0ba3b-113">[Nasıl yapılır: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ba3b-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="0ba3b-114">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="0ba3b-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="0ba3b-115">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="0ba3b-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="0ba3b-116">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="0ba3b-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="0ba3b-117">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="0ba3b-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="0ba3b-118">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="0ba3b-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="0ba3b-119">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="0ba3b-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
