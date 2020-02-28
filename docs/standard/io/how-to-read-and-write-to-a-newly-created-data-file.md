---
title: 'Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma'
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155756"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="13b02-102">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="13b02-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="13b02-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışında veri yazmak ve okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13b02-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="13b02-104">Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulacağını, verilerin nasıl yazılacağını ve verilerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="13b02-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="13b02-105">Örnek, geçerli dizinde *test. Data* adlı bir veri dosyası oluşturur, ilişkili <xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader> nesneleri oluşturur ve dosya işaretçisini dosyanın *sonunda bırakmak üzere*0 ' dan 10 ' a kadar olan tamsayıları yazmak için <xref:System.IO.BinaryWriter> nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="13b02-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="13b02-106"><xref:System.IO.BinaryReader> nesnesi sonra dosya işaretçisini kaynağa geri ayarlar ve belirtilen içeriği okur.</span><span class="sxs-lookup"><span data-stu-id="13b02-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13b02-107">Eğer *test. Data* geçerli dizinde zaten mevcutsa, bir <xref:System.IO.IOException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="13b02-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="13b02-108">Özel durum oluşturmadan her zaman yeni bir dosya oluşturmak için <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> yerine <xref:System.IO.FileMode.Create?displayProperty=nameWithType> dosya modu seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="13b02-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b02-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="13b02-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="13b02-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13b02-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="13b02-111">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="13b02-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="13b02-112">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="13b02-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="13b02-113">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="13b02-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="13b02-114">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="13b02-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="13b02-115">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="13b02-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="13b02-116">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="13b02-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="13b02-117">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="13b02-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
