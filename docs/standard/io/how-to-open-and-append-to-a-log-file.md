---
title: "Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333b20adee4ea2826a1fc6795a39490dca1af843
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="49a1f-102">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="49a1f-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="49a1f-103"><xref:System.IO.StreamWriter>ve <xref:System.IO.StreamReader> karakterleri yazmak ve akışlardan karakterleri okuma.</span><span class="sxs-lookup"><span data-stu-id="49a1f-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="49a1f-104">Aşağıdaki kod örnek açılır `log.txt` dosya için giriş veya zaten mevcut değilse ve bilgi dosyasının sonuna ekler dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49a1f-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="49a1f-105">Ardından dosyasının içeriğini görüntülemek için standart çıktı yazılır.</span><span class="sxs-lookup"><span data-stu-id="49a1f-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="49a1f-106">Bu örnek için alternatif olarak, bilgileri tek bir dize veya dize dizisi olarak depolanabilir ve <xref:System.IO.File.WriteAllText%2A> veya <xref:System.IO.File.WriteAllLines%2A> yöntemi aynı işlevselliği elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49a1f-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49a1f-107">Visual Basic kullanıcıları tarafından sağlanan özellikler ve yöntemler kullanmayı seçebilir <xref:Microsoft.VisualBasic.Logging.Log> sınıfı veya <xref:Microsoft.VisualBasic.FileIO.FileSystem> oluşturmak veya günlük dosyaları yazma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49a1f-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49a1f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="49a1f-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="49a1f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49a1f-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="49a1f-110">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="49a1f-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="49a1f-111">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="49a1f-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="49a1f-112">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="49a1f-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="49a1f-113">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="49a1f-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="49a1f-114">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="49a1f-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="49a1f-115">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="49a1f-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="49a1f-116">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="49a1f-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
