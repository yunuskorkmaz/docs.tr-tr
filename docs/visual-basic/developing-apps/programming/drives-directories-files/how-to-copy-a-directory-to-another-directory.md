---
title: 'Nasıl Yapılır: Bir Dizini Diğerine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348858"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama

Bir <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> dizini başka bir dizine kopyalamak için yöntemi kullanın. Bu yöntem, dizinin içeriğini ve dizinin kendisini kopyalar. Hedef dizini yoksa, oluşturulur. Hedef konumda aynı ada sahip bir dizin varsa ve `overwrite` `False`ayarlanmışsa, iki dizinin içeriği birleştirilir. İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.

Bir dizin içinde dosyaları kopyalarken, birleştirme `overwrite` sırasında var olan dosya gibi belirli bir dosyanın `False`neden olduğu özel durumlar atılabilir. Bu tür özel durumlar atıldığında, özelliği dosya veya `Data` dizin yolunun anahtar olduğu ve belirli özel durum iletisinin ilgili değerde bulunduğu girişleri barındıran tek bir özel durum olarak birleştirilir.

## <a name="to-copy-a-directory-to-another-directory"></a>Bir dizini başka bir dizine kopyalamak için

- Kaynak `CopyDirectory` ve hedef dizin adlarını belirterek yöntemi kullanın. Aşağıdaki örnek, varolan dosyaların `TestDirectory1` `TestDirectory2`üzerine yazdığı dizini kopyalar.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, dosya sisteminde yer alır **- İşleme Sürücüler, Klasörler ve Dosyalar**. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Dizin için belirtilen yeni ad bir üst üste (:) veya eğik çizgi (\ veya /) (<xref:System.ArgumentException>).

- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).

- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).

- `destinationDirectoryName`veya `Nothing` boş bir<xref:System.ArgumentNullException>dize ( )

- Kaynak dizini yok (<xref:System.IO.DirectoryNotFoundException>).

- Kaynak dizini bir kök dizinidir (<xref:System.IO.IOException>).

- Birleştirilmiş yol varolan bir<xref:System.IO.IOException>dosyayı işaret eder ( ).

- Kaynak yolu ve hedef yolu<xref:System.IO.IOException>aynıdır ( ).

- `ShowUI`ayarlanır `UIOption.AllDialogs` ve kullanıcı işlemi iptal eder veya dizindeki bir veya daha fazla<xref:System.OperationCanceledException>dosya kopyalanamaz ( ).

- İşlem döngüseldir (<xref:System.InvalidOperationException>).

- Yol bir kolon içerir (:) (<xref:System.NotSupportedException>).

- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).

- Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).

- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).

- Hedef dosya var, ancak erişilemiyor (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
