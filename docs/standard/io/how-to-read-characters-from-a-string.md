---
title: 'Nasıl yapılır: dizeden karakterleri okuma'
description: .NET 'teki bir dizeden karakter okumayı öğrenin. Zaman uyumlu ve zaman uyumsuz karakter okuma örneklerine bakın.
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
ms.openlocfilehash: fa03d13036e9e245b8ca3f8c3218ae80a2762a12
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553954"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="e5906-104">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="e5906-104">How to: Read characters from a string</span></span>
<span data-ttu-id="e5906-105">Aşağıdaki kod örnekleri, bir dizeden zaman uyumlu veya zaman uyumsuz karakterlerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5906-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="e5906-106">Örnek: karakterleri zaman uyumlu olarak okuyun</span><span class="sxs-lookup"><span data-stu-id="e5906-106">Example: Read characters synchronously</span></span>
 <span data-ttu-id="e5906-107">Bu örnek, bir dizeden zaman uyumlu olarak 13 karakter okur, bunları bir dizide depolar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5906-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="e5906-108">Örnek daha sonra dizedeki karakterlerin geri kalanını okur, bunları altıncı öğeden başlayarak dizide depolar ve dizinin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5906-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="e5906-109">Örnek: karakterleri zaman uyumsuz olarak oku</span><span class="sxs-lookup"><span data-stu-id="e5906-109">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="e5906-110">Sonraki örnek, bir WPF uygulamasının arkasındaki koddur.</span><span class="sxs-lookup"><span data-stu-id="e5906-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="e5906-111">Pencere yükleme sırasında örnek, bir denetimdeki tüm karakterleri zaman uyumsuz olarak okur <xref:System.Windows.Controls.TextBox> ve bunları bir dizide depolar.</span><span class="sxs-lookup"><span data-stu-id="e5906-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="e5906-112">Ardından, her bir harfi veya boşluk karakterini bir denetimin ayrı bir satırına zaman uyumsuz olarak yazar <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="e5906-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e5906-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5906-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="e5906-114">Zaman uyumsuz dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="e5906-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="e5906-115">[Nasıl yapılır: Dizin listesi oluşturma](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5906-115">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="e5906-116">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="e5906-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="e5906-117">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="e5906-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="e5906-118">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="e5906-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="e5906-119">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="e5906-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="e5906-120">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="e5906-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="e5906-121">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="e5906-121">File and stream I/O</span></span>](index.md)
