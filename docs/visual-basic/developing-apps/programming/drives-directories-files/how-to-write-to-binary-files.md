---
title: 'Nasıl yapılır: Visual Basic Ikili dosyalara yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: ab42fa50aaf39397ac51db8a4cc3a3b00f6ce878
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039412"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic Ikili dosyalara yazma

Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> , verileri bir ikili dosyaya yazar. `append` Parametresi ise`True`, verileri dosyaya ekler; Aksi halde dosyadaki verilerin üzerine yazılır.

Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur. Yol geçerliyse ancak dosya yoksa dosya oluşturulur.

## <a name="to-write-to-a-binary-file"></a>İkili bir dosyaya yazmak için

Dosya yolu ve adı ve yazılacak baytları sağlayarak yönteminikullanın.`WriteAllBytes` Bu örnek, veri dizisini `CustomerData` adlı `CollectedData.dat`dosyaya ekler.

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
- [Nasıl yapılır: Dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
