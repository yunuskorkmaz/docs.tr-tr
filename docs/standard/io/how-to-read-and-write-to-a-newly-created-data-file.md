---
title: 'Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 65c56a11531f705b7e047e435ec575969d39a616
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187682"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="1c482-102">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="1c482-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="1c482-103"><xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri yerine verileri yazmak ve okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c482-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="1c482-104">Aşağıdaki örnek, `Test.data` adındaki yeni ve boş bir dosya akışına verilerin nasıl yazılacağını ve bu dosya akışındaki verilerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c482-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="1c482-105">Veri dosyasını geçerli dizinde oluşturduktan sonra, ilişkili <xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader> nesneleri oluşturulur ve <xref:System.IO.BinaryWriter> nesnesi, 0 ile 10 arasındaki tamsayıları, dosya işaretçisini dosyanın sonunda bırakan  `Test.data`'a yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c482-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="1c482-106">Dosya işaretçisini başlangıç noktasına geri ayarladıktan sonra <xref:System.IO.BinaryReader> nesnesi belirtilen içeriği okur.</span><span class="sxs-lookup"><span data-stu-id="1c482-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c482-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c482-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1c482-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1c482-108">Robust Programming</span></span>  
 <span data-ttu-id="1c482-109">Eğer `Test.data` geçerli dizinde zaten bulunuyorsa, bir <xref:System.IO.IOException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1c482-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="1c482-110">Özel durum oluşturmadan her zaman yeni bir dosya oluşturmak için, dosya akışını başlatırken <xref:System.IO.FileMode.Create?displayProperty=nameWithType> dosya modu seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c482-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c482-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c482-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="1c482-112">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="1c482-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="1c482-113">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="1c482-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="1c482-114">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="1c482-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="1c482-115">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="1c482-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="1c482-116">Nasıl yapılır: Dizeden Karakterleri Okuma</span><span class="sxs-lookup"><span data-stu-id="1c482-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="1c482-117">Nasıl yapılır: Bir Dizeye Karakter Yazma</span><span class="sxs-lookup"><span data-stu-id="1c482-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="1c482-118">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="1c482-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
