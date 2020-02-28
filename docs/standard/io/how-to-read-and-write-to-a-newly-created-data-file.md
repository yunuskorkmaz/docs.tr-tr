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
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma
<xref:System.IO.BinaryWriter?displayProperty=nameWithType> ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışında veri yazmak ve okumak için kullanılır. Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulacağını, verilerin nasıl yazılacağını ve verilerin nasıl okunacağını gösterir.

Örnek, geçerli dizinde *test. Data* adlı bir veri dosyası oluşturur, ilişkili <xref:System.IO.BinaryWriter> ve <xref:System.IO.BinaryReader> nesneleri oluşturur ve dosya işaretçisini dosyanın *sonunda bırakmak üzere*0 ' dan 10 ' a kadar olan tamsayıları yazmak için <xref:System.IO.BinaryWriter> nesnesini kullanır. <xref:System.IO.BinaryReader> nesnesi sonra dosya işaretçisini kaynağa geri ayarlar ve belirtilen içeriği okur.  
  
> [!NOTE]
> Eğer *test. Data* geçerli dizinde zaten mevcutsa, bir <xref:System.IO.IOException> özel durumu oluşturulur. Özel durum oluşturmadan her zaman yeni bir dosya oluşturmak için <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> yerine <xref:System.IO.FileMode.Create?displayProperty=nameWithType> dosya modu seçeneğini kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
