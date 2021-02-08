---
description: 'Daha fazla bilgi: nasıl yapılır: Visual Basic Ikili dosyalara yazma'
title: 'Nasıl yapılır: İkili Dosyalara Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: a1fe18c9143c26fd40e6a1d9cde36581c2c0be12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797334"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Yöntemi, verileri bir ikili dosyaya yazar. `append`Parametresi ise `True` , verileri dosyaya ekler; Aksi halde dosyadaki verilerin üzerine yazılır.

Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur. Yol geçerliyse ancak dosya yoksa dosya oluşturulur.

## <a name="to-write-to-a-binary-file"></a>İkili bir dosyaya yazmak için

`WriteAllBytes`Dosya yolu ve adı ve yazılacak baytları sağlayarak yöntemini kullanın. Bu örnek, veri dizisini `CustomerData` adlı dosyaya ekler `CollectedData.dat` .

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar bir özel durum oluşturabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor. (<xref:System.ArgumentException>).

- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .

- `File` varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).

- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.

- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).

- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Nasıl yapılır: Dosyalara Metin Yazma](how-to-write-text-to-files.md)
