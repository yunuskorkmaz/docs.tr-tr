---
title: 'Nasıl yapılır: Bir dizini Visual Basic başka bir dizine kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: d8f32da0f4b701d745cd5f70feb7cc461a09842f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039464"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Nasıl yapılır: Bir dizini Visual Basic başka bir dizine kopyalama

Bir dizini başka bir dizine kopyalamak için yönteminikullanın.<xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> Bu yöntem, dizinin içeriğini ve dizinin kendisini kopyalar. Hedef dizin yoksa, oluşturulur. Hedef konumda aynı ada sahip bir dizin varsa ve `overwrite` olarak `False`ayarlanırsa, iki dizinin içeriği birleştirilir. İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.

Dosyaları bir dizin içinde kopyalarken, özel bir dosya (örneğin, birleştirme `overwrite` `False`sırasında var olan bir dosya gibi) nedeniyle özel durumlar oluşturulabilir. Bu tür özel durumlar oluştuğunda, `Data` özelliği dosya veya dizin yolunun anahtar olduğu ve belirli özel durum iletisinin karşılık gelen değerde bulunduğu girdileri tutan tek bir özel durum halinde birleştirilir.

## <a name="to-copy-a-directory-to-another-directory"></a>Bir dizini başka bir dizine kopyalamak için

- Kaynak ve hedef dizin adlarını belirterek yönteminikullanın.`CopyDirectory` Aşağıdaki örnek, var olan dosyaların üzerine `TestDirectory1` yazarak `TestDirectory2`adlı dizini içine kopyalar.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide **dosya sistemi Işleme sürücülerinde, klasörlerinde ve dosyalarında**bulunur. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Dizin için belirtilen yeni ad iki nokta içerir (:) veya eğik çizgi (\ veya/)<xref:System.ArgumentException>().

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.

- `destinationDirectoryName`ya da boş bir dize (<xref:System.ArgumentNullException>) `Nothing`

- Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).

- Kaynak dizin bir kök dizin (<xref:System.IO.IOException>).

- Birleşik yol, var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.

- Kaynak yolu ve hedef yolu aynı (<xref:System.IO.IOException>).

- `ShowUI`, olarak `UIOption.AllDialogs` ayarlanır ve Kullanıcı işlemi iptal eder veya dizindeki bir veya daha fazla Dosya kopyalanamıyor (<xref:System.OperationCanceledException>).

- İşlem döngüsel (<xref:System.InvalidOperationException>).

- Yol iki nokta içerir (:) (<xref:System.NotSupportedException>).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.

- Hedef dosya var, ancak erişilemez (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Nasıl yapılır: Belirli bir düzene sahip alt dizinler bulun](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Nasıl yapılır: Dizindeki dosyaların toplanmasını al](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
