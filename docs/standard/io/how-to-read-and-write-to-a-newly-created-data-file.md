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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947218"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma
<xref:System.IO.BinaryWriter?displayProperty=nameWithType> Ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışındaki verileri yazmak ve okumak için kullanılır. Aşağıdaki örnek, bir boş bir dosya akışı oluşturma, veri yazma ve ondan veri okumak gösterilmektedir. 

Örnek adlı bir veri dosyası oluşturur *Test.data* ilişkili geçerli dizinde oluşturur <xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader> nesneleri ve kullandığı <xref:System.IO.BinaryWriter> için0ile10arasındakitamsayılarıyazılacaknesne*Test.data*, dosya işaretçisini dosyanın sonunda bırakan. <xref:System.IO.BinaryReader> Nesne sonra dosya işaretçisini başlangıç noktasına geri ayarlar ve belirtilen içeriği okur.  
  
> [!NOTE]
> Varsa *Test.data* geçerli dizinde zaten var. bir <xref:System.IO.IOException> özel durumu oluşturulur. Dosya modu seçeneğini kullanın <xref:System.IO.FileMode.Create?displayProperty=nameWithType> yerine <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> her zaman bir özel durum olmadan yeni bir dosya oluşturmak için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Nasıl yapılır: Dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: Bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: Dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: Bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
