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

Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> , verileri bir ikili dosyaya yazar. `append` Parametresi ise `True`, verileri dosyaya ekler; Aksi takdirde, dosyadaki verilerin üzerine yazılır.

Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur. Yol geçerliyse ancak dosya yoksa dosya oluşturulur.

## <a name="to-write-to-a-binary-file"></a>İkili bir dosyaya yazmak için

Dosya yolu `WriteAllBytes` ve adı ve yazılacak baytları sağlayarak yöntemini kullanın. Bu örnek, veri dizisini `CustomerData` adlı `CollectedData.dat`dosyaya ekler.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar bir özel durum oluşturabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor. (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.

- `File`varolmayan bir yola işaret eder (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).

- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu (<xref:System.IO.IOException>).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Nasıl Yapılır: Dosyalara Metin Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
