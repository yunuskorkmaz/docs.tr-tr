---
title: "Nasıl yapılır: Bir Dizeye Karakter Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d409b9f9cada319c64c4b5a1315b8a5abbd731e9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="5a700-102">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="5a700-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="5a700-103">Aşağıdaki kod örnekleri karakter zaman uyumlu ve zaman uyumsuz olarak karakter dizisinden bir dize olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="5a700-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a700-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a700-104">Example</span></span>  
 <span data-ttu-id="5a700-105">Aşağıdaki örnek 5 karakter dizeye dizisinden zaman uyumlu olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="5a700-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="5a700-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a700-106">Example</span></span>  
 <span data-ttu-id="5a700-107">Sonraki örnekte tüm karakterler zaman uyumsuz olarak okur bir <xref:System.Windows.Controls.TextBox> denetleyen ve bunları bir dizide depolar.</span><span class="sxs-lookup"><span data-stu-id="5a700-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="5a700-108">Ardından zaman uyumsuz olarak her harf ya da boşluk karakteri bir satır sonu arkasından ayrı bir satırda Yazar bir <xref:System.Windows.Controls.TextBlock> denetim.</span><span class="sxs-lookup"><span data-stu-id="5a700-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5a700-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a700-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="5a700-110">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="5a700-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="5a700-111">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="5a700-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="5a700-112">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="5a700-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="5a700-113">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="5a700-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="5a700-114">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="5a700-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="5a700-115">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="5a700-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="5a700-116">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="5a700-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="5a700-117">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="5a700-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
