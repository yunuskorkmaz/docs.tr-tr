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
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma
<xref:System.IO.BinaryWriter?displayProperty=nameWithType>Ve <xref:System.IO.BinaryReader?displayProperty=nameWithType> sınıfları, karakter dizeleri dışında veri yazmak ve okumak için kullanılır. Aşağıdaki örnek, boş bir dosya akışının nasıl oluşturulacağını, verilerin nasıl yazılacağını ve verilerin nasıl okunacağını gösterir.

Örnek, geçerli dizinde *test. Data* adlı bir veri dosyası oluşturur, ilişkili <xref:System.IO.BinaryWriter> ve nesneleri oluşturur ve dosya <xref:System.IO.BinaryReader> <xref:System.IO.BinaryWriter> işaretçisini dosyanın sonunda bırakmak için 0 ' dan 10 ' a kadar olan tamsayıları *Test.data*yazmak için nesnesini kullanır. <xref:System.IO.BinaryReader>Ardından nesne, dosya işaretçisini kaynağa geri ayarlar ve belirtilen içeriği okur.  
  
> [!NOTE]
> Eğer *test. Data* geçerli dizinde zaten mevcutsa, bir <xref:System.IO.IOException> özel durum oluşturulur. <xref:System.IO.FileMode.Create?displayProperty=nameWithType> <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> Özel durum oluşturmadan her zaman yeni bir dosya oluşturmak yerine dosya modu seçeneğini kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: dosyadan metin okuma](how-to-read-text-from-a-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](index.md)
