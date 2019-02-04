---
title: 'Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 065907ae0d4a38ff2ef68de6025251e28220ee96
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674626"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="b3ed3-102">Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="b3ed3-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> Ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışındaki verileri yazmak ve okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="b3ed3-104">Aşağıdaki örnek, bir boş bir dosya akışı oluşturma, veri yazma ve ondan veri okumak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span> 

<span data-ttu-id="b3ed3-105">Örnek adlı bir veri dosyası oluşturur *Test.data* ilişkili geçerli dizinde oluşturur <xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader> nesneleri ve kullandığı <xref:System.IO.BinaryWriter> için0ile10arasındakitamsayılarıyazılacaknesne*Test.data*, dosya işaretçisini dosyanın sonunda bırakan.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="b3ed3-106"><xref:System.IO.BinaryReader> Nesne sonra dosya işaretçisini başlangıç noktasına geri ayarlar ve belirtilen içeriği okur.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3ed3-107">Varsa *Test.data* geçerli dizinde zaten var. bir <xref:System.IO.IOException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="b3ed3-108">Dosya modu seçeneğini kullanın <xref:System.IO.FileMode.Create?displayProperty=nameWithType> yerine <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> her zaman bir özel durum olmadan yeni bir dosya oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3ed3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ed3-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b3ed3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3ed3-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="b3ed3-111">Nasıl yapılır: Dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="b3ed3-112">Nasıl yapılır: Açın ve bir günlük dosyasına Ekle</span><span class="sxs-lookup"><span data-stu-id="b3ed3-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="b3ed3-113">Nasıl yapılır: Bir dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="b3ed3-114">Nasıl yapılır: Bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="b3ed3-115">Nasıl yapılır: Dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="b3ed3-116">Nasıl yapılır: Bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="b3ed3-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="b3ed3-117">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="b3ed3-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
