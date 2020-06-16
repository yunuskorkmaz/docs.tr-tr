---
title: 'Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma'
description: System. ıO. BinaryReader ve System. ıO. BinaryWriter sınıflarını kullanarak .NET 'teki yeni oluşturulan bir veri dosyasını okuma ve yazma hakkında bilgi edinin.
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
ms.openlocfilehash: 9a6b2985b7f532476c0f4c0f998d710f95e55d3a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769164"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="f4e6e-103">Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-103">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="f4e6e-104"><xref:System.IO.BinaryWriter?displayProperty=nameWithType>Ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışında veri yazmak ve okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-104">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="f4e6e-105">Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulacağını, verilerin nasıl yazılacağını ve verilerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-105">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="f4e6e-106">Örnek, geçerli dizinde *test. Data* adlı bir veri dosyası oluşturur, ilişkili <xref:System.IO.BinaryWriter> ve nesneleri oluşturur ve dosya <xref:System.IO.BinaryReader> <xref:System.IO.BinaryWriter> işaretçisini dosyanın sonunda bırakmak için 0 ' dan 10 ' a kadar olan tamsayıları *Test.data*yazmak için nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-106">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="f4e6e-107"><xref:System.IO.BinaryReader>Ardından nesne, dosya işaretçisini kaynağa geri ayarlar ve belirtilen içeriği okur.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-107">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4e6e-108">Eğer *test. Data* geçerli dizinde zaten mevcutsa, bir <xref:System.IO.IOException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-108">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="f4e6e-109"><xref:System.IO.FileMode.Create?displayProperty=nameWithType> <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> Özel durum oluşturmadan her zaman yeni bir dosya oluşturmak yerine dosya modu seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-109">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4e6e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4e6e-110">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="f4e6e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="f4e6e-112">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-112">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="f4e6e-113">Nasıl yapılır: günlük dosyasını açma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="f4e6e-113">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="f4e6e-114">Nasıl yapılır: dosyadan metin okuma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-114">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="f4e6e-115">Nasıl yapılır: bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-115">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="f4e6e-116">Nasıl yapılır: dizeden karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-116">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="f4e6e-117">Nasıl yapılır: bir dizeye karakter yazma</span><span class="sxs-lookup"><span data-stu-id="f4e6e-117">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="f4e6e-118">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="f4e6e-118">File and stream I/O</span></span>](index.md)
