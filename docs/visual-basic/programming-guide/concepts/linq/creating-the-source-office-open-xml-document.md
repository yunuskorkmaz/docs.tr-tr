---
title: Kaynak Office Open XML belgesi (Visual Basic) oluşturma
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 83cb7d0a325e11c9669f1331e57bed7bf09f27c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333697"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Kaynak Office Open XML belgesi (Visual Basic) oluşturma
Bu konu, diğer bu öğreticideki örneklerde Office Open XML WordprocessingML belgesi nasıl oluşturacağınızı gösterir. Bu yönergeleri izleyin, çıkış her örnekte sağlanan çıkış eşleşir.  
  
 Ancak, bu öğreticideki örneklerde, geçerli bir WordprocessingML belgesi ile çalışır.  
  
 Bu öğreticide bir belge oluşturmak için ya da Microsoft Office 2007 yüklü olmalıdır veya sonraki bir sürümünün yüklü veya Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturmak için  
  
1. Yeni bir Microsoft Word belgesi oluşturun.  
  
2. Aşağıdaki metni yeni bir belgeye yapıştırın:  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. İlk satır stili "Başlık 1" ile biçimlendirin.  
  
4. Visual Basic kodunu içeren satırları seçin. İlk satırı ile başlayan `Imports` anahtar sözcüğü. Son satırı "End Class" dir. Satırları courier yazı biçimi. İle yeni bir stil biçimlendirir ve yeni stil "Code" olarak adlandırın.  
  
5. Son olarak, çıktısını içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.  
  
6. Belgeyi kaydedin ve SampleDoc.docx adlandırın.  
  
    > [!NOTE]
    >  Microsoft Word 2003 kullanıyorsanız **Word 2007 belgesi** içinde **farklı kaydetme türü** aşağı açılan listesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
