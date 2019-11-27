---
title: 'Nasıl Yapılır: İkili Dosyalara Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334427"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> yöntemi, verileri bir ikili dosyaya yazar. `append` parametresi `True`, verileri dosyaya ekler; Aksi takdirde, dosyadaki verilerin üzerine yazılır.

Dosya adı hariç belirtilen yol geçerli değilse, <xref:System.IO.DirectoryNotFoundException> bir özel durum oluşturulur. Yol geçerliyse ancak dosya yoksa dosya oluşturulur.

## <a name="to-write-to-a-binary-file"></a>İkili bir dosyaya yazmak için

Dosya yolu ve adı ve yazılacak baytları sağlayarak `WriteAllBytes` yöntemini kullanın. Bu örnek `CustomerData` veri dizisini `CollectedData.dat`adlı dosyaya ekler.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar bir özel durum oluşturabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor. (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.

- `File`, varolmayan bir yola işaret eder (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).

- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu (<xref:System.IO.IOException>).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Nasıl Yapılır: Dosyalara Metin Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
