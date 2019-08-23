---
title: Kaynak Office Open XML belgesi (Visual Basic) oluşturuluyor
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: d01755442a9b64e0577ace4eb05c6818dac9a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965247"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Kaynak Office Open XML belgesi (Visual Basic) oluşturuluyor
Bu konu başlığında, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağı gösterilmektedir. Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.  
  
 Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.  
  
 Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturmak için  
  
1. Yeni bir Microsoft Word belgesi oluşturun.  
  
2. Aşağıdaki metni yeni belgeye yapıştırın:  
  
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
  
3. İlk satırı "Başlık 1" stiliyle biçimlendirin.  
  
4. Visual Basic kodunu içeren satırları seçin. İlk satır `Imports` anahtar sözcüğüyle başlar. Son satır "End Class" dır. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.  
  
5. Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.  
  
6. Belgeyi kaydedin ve SampleDoc. docx olarak adlandırın.  
  
    > [!NOTE]
    > Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
