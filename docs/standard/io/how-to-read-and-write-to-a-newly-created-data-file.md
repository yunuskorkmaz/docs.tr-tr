---
title: 'Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155756"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="5a72b-102">Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="5a72b-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="5a72b-103">Ve <xref:System.IO.BinaryWriter?displayProperty=nameWithType> <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıflar, karakter dizeleri dışındaki verileri yazmak ve okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a72b-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="5a72b-104">Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulup, ona veri yazmanın ve ondan gelen verilerin nasıl okunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a72b-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="5a72b-105">Örnek, geçerli dizinde *Test.data* adlı bir veri dosyası <xref:System.IO.BinaryWriter> oluşturur, <xref:System.IO.BinaryReader> ilişkili ve nesneleri <xref:System.IO.BinaryWriter> oluşturur ve dosya işaretçisini dosyanın sonunda bırakan 0 ile 10 arasında test verisine tamsayılar yazmak *için*nesneyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a72b-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="5a72b-106">Nesne <xref:System.IO.BinaryReader> daha sonra dosya işaretçisini menşeine geri ayarlar ve belirtilen içeriği okur.</span><span class="sxs-lookup"><span data-stu-id="5a72b-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a72b-107">*Test.data* geçerli dizinde zaten varsa, <xref:System.IO.IOException> bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="5a72b-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="5a72b-108">Her zaman bir <xref:System.IO.FileMode.Create?displayProperty=nameWithType> özel <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> durum oluşturmadan yeni bir dosya oluşturmak yerine dosya modu seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a72b-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a72b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a72b-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5a72b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a72b-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="5a72b-111">Nasıl yapılır: Dizinleri ve dosyaları sayısal</span><span class="sxs-lookup"><span data-stu-id="5a72b-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="5a72b-112">Nasıl yapılı: Günlük dosyasını açma ve ekle</span><span class="sxs-lookup"><span data-stu-id="5a72b-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="5a72b-113">Nasıl yapilir: Dosyadaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="5a72b-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="5a72b-114">Nasıl yazılır: Dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="5a72b-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="5a72b-115">Nasıl yapilir: Bir dizedeki karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="5a72b-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="5a72b-116">Nasıl yazılır: Karakterleri bir dize yazma</span><span class="sxs-lookup"><span data-stu-id="5a72b-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="5a72b-117">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="5a72b-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
