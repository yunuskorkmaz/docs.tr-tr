---
title: 'Nasıl yapılı: Günlük dosyasını açma ve ekle'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155717"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="444cf-102">Nasıl yapılı: Günlük dosyasını açma ve ekle</span><span class="sxs-lookup"><span data-stu-id="444cf-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="444cf-103"><xref:System.IO.StreamWriter>ve <xref:System.IO.StreamReader> karakterleryazmak ve akışları karakterleri okuyun.</span><span class="sxs-lookup"><span data-stu-id="444cf-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="444cf-104">Aşağıdaki kod örneği giriş için *log.txt* dosyasını açar veya yoksa oluşturur ve günlük bilgilerini dosyanın sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="444cf-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="444cf-105">Örnek daha sonra dosyanın içeriğini görüntülemek için standart çıktıya yazar.</span><span class="sxs-lookup"><span data-stu-id="444cf-105">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="444cf-106">Bu örneğe alternatif olarak, bilgileri tek bir dize veya dize <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> dizisi olarak depolayabilir ve aynı işlevselliği elde etmek için veya yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="444cf-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="444cf-107">Visual Basic kullanıcıları, dosyaları oluşturmak veya yazmak <xref:Microsoft.VisualBasic.Logging.Log> için <xref:Microsoft.VisualBasic.FileIO.FileSystem> sınıf veya sınıf tarafından sağlanan yöntemleri ve özellikleri kullanmayı seçebilir.</span><span class="sxs-lookup"><span data-stu-id="444cf-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="444cf-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="444cf-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="444cf-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="444cf-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="444cf-110">Nasıl yapılır: Dizinleri ve dosyaları sayısal</span><span class="sxs-lookup"><span data-stu-id="444cf-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="444cf-111">Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="444cf-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="444cf-112">Nasıl yapilir: Dosyadaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="444cf-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="444cf-113">Nasıl yazılır: Dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="444cf-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="444cf-114">Nasıl yapilir: Bir dizedeki karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="444cf-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="444cf-115">Nasıl yazılır: Karakterleri bir dize yazma</span><span class="sxs-lookup"><span data-stu-id="444cf-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="444cf-116">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="444cf-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
