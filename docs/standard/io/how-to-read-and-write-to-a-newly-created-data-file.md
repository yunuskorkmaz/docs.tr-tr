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
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma
Ve <xref:System.IO.BinaryWriter?displayProperty=nameWithType> <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıflar, karakter dizeleri dışındaki verileri yazmak ve okumak için kullanılır. Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulup, ona veri yazmanın ve ondan gelen verilerin nasıl okunduğunu gösterir.

Örnek, geçerli dizinde *Test.data* adlı bir veri dosyası <xref:System.IO.BinaryWriter> oluşturur, <xref:System.IO.BinaryReader> ilişkili ve nesneleri <xref:System.IO.BinaryWriter> oluşturur ve dosya işaretçisini dosyanın sonunda bırakan 0 ile 10 arasında test verisine tamsayılar yazmak *için*nesneyi kullanır. Nesne <xref:System.IO.BinaryReader> daha sonra dosya işaretçisini menşeine geri ayarlar ve belirtilen içeriği okur.  
  
> [!NOTE]
> *Test.data* geçerli dizinde zaten varsa, <xref:System.IO.IOException> bir özel durum atılır. Her zaman bir <xref:System.IO.FileMode.Create?displayProperty=nameWithType> özel <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> durum oluşturmadan yeni bir dosya oluşturmak yerine dosya modu seçeneğini kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Nasıl yapılır: Dizinleri ve dosyaları sayısal](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılı: Günlük dosyasını açma ve ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapilir: Dosyadaki metni okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Nasıl yazılır: Dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapilir: Bir dizedeki karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yazılır: Karakterleri bir dize yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
