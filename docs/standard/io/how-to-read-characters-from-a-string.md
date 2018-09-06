---
title: 'Nasıl yapılır: Dizeden Karakterleri Okuma'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13a57f8ea7db91e5357ecfb20c4e907f2706f78d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871078"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="09f7e-102">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="09f7e-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="09f7e-103">Aşağıdaki kod örnekleri, zaman uyumlu ve zaman uyumsuz olarak bir dizeden karakterleri okuma işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="09f7e-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09f7e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="09f7e-104">Example</span></span>  
 <span data-ttu-id="09f7e-105">Bu örnekte 13 karakter zaman uyumlu olarak dize, bunları bir dizide saklar ve bu karakterleri okur.</span><span class="sxs-lookup"><span data-stu-id="09f7e-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="09f7e-106">Ardından kalan karakter dizesini okur, altıncı öğe başlangıç dizisi depolar ve dizinin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="09f7e-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="09f7e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="09f7e-107">Example</span></span>  
 <span data-ttu-id="09f7e-108">Sonraki örnek, zaman uyumsuz olarak öğesindeki tüm karakterleri okur bir <xref:System.Windows.Controls.TextBox> denetlemek ve bunları bir dizide saklar.</span><span class="sxs-lookup"><span data-stu-id="09f7e-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="09f7e-109">Ardından zaman uyumsuz olarak her bir harf veya boşluk karakteri için bir satır sonu ardından ayrı bir satırda Yazar bir <xref:System.Windows.Controls.TextBlock> denetimi.</span><span class="sxs-lookup"><span data-stu-id="09f7e-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="09f7e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09f7e-110">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="09f7e-111">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="09f7e-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="09f7e-112">NIB: Nasıl yapılır: Create a Directory Listing</span><span class="sxs-lookup"><span data-stu-id="09f7e-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="09f7e-113">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="09f7e-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="09f7e-114">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="09f7e-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="09f7e-115">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="09f7e-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="09f7e-116">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="09f7e-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="09f7e-117">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="09f7e-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="09f7e-118">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="09f7e-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
