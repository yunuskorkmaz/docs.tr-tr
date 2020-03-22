---
title: 'Nasıl Yapılır: İkili Dosyalara Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334427"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma

Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> verileri ikili bir dosyaya yazar. `append` Parametre ise, `True`verileri dosyaya ekler; aksi takdirde dosyadaki veriler üzerine yazılır.

Dosya adı hariç belirtilen yol geçerli değilse, <xref:System.IO.DirectoryNotFoundException> bir özel durum atılır. Yol geçerliyse ancak dosya yoksa, dosya oluşturulur.

## <a name="to-write-to-a-binary-file"></a>İkili dosyaya yazmak için

Dosya `WriteAllBytes` yolunu ve adını ve yazılacak baytları sağlayarak yöntemi kullanın. Bu örnek, veri `CustomerData` dizisini adlı `CollectedData.dat`dosyaya ekler.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar bir özel durum oluşturabilir:

- Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunlukta bir dizedir; sadece beyaz boşluk içerir; veya geçersiz karakterler içerir. (<xref:System.ArgumentException>).

- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).

- `File`olmayan bir yola işaret eder<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>( veya ).

- Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).

- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).

- Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).

- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Nasıl Yapılır: Dosyalara Metin Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
