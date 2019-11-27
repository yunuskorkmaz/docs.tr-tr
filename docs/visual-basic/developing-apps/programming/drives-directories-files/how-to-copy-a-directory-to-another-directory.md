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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348858"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama

Bir dizini başka bir dizine kopyalamak için <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> yöntemini kullanın. Bu yöntem, dizinin içeriğini ve dizinin kendisini kopyalar. Hedef dizin yoksa, oluşturulur. Hedef konumda aynı ada sahip bir dizin varsa ve `overwrite` `False`olarak ayarlanırsa, iki dizinin içeriği birleştirilir. İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.

Dosyalar bir dizin içinde kopyalanırken, bir birleştirme sırasında var olan bir dosya gibi belirli bir dosya (örneğin, `overwrite` `False`olarak ayarlandığında) özel durumlar oluşturulabilir. Bu tür özel durumlar oluştuğunda, `Data` özelliği dosya veya dizin yolunun anahtar olduğu ve belirli özel durum iletisinin karşılık gelen değerde bulunduğu girdileri tutan tek bir özel durum halinde birleştirilir.

## <a name="to-copy-a-directory-to-another-directory"></a>Bir dizini başka bir dizine kopyalamak için

- Kaynak ve hedef dizin adlarını belirterek `CopyDirectory` yöntemini kullanın. Aşağıdaki örnek, `TestDirectory1` adlı dizini var olan dosyaların üzerine yazarak `TestDirectory2`kopyalar.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Dizin için belirtilen yeni ad iki nokta içerir (:) veya eğik çizgi (\ veya/) (<xref:System.ArgumentException>).

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.

- `destinationDirectoryName` `Nothing` veya boş bir dize (<xref:System.ArgumentNullException>)

- Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).

- Kaynak dizin bir kök dizin (<xref:System.IO.IOException>).

- Birleşik yol, var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.

- Kaynak yolu ve hedef yolu aynı (<xref:System.IO.IOException>).

- `ShowUI` `UIOption.AllDialogs` olarak ayarlanır ve Kullanıcı işlemi iptal eder veya dizindeki bir veya daha fazla Dosya kopyalanamıyor (<xref:System.OperationCanceledException>).

- İşlem döngüsel (<xref:System.InvalidOperationException>).

- Yol iki nokta içerir (:) (<xref:System.NotSupportedException>).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).

- Hedef dosya var, ancak erişilemez (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
