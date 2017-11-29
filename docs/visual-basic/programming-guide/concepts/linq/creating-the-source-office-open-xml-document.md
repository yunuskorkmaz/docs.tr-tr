---
title: "Kaynak Office Açık XML belge (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c573f703ea3d7550dabd994f538e28e197874715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Kaynak Office Açık XML belge (Visual Basic) oluşturma
Bu konu diğer örnekleri Bu öğreticide kullanmak Office Açık XML WordprocessingML belgesi nasıl oluşturacağınızı gösterir. Bu yönergeleri izleyin, her örnekte sağlanan çıkış, çıktı eşleşir.  
  
 Ancak, Bu öğretici örneklerde sahip herhangi bir geçerli WordprocessingML belgeyi çalışır.  
  
 Bu öğretici kullanır belge oluşturmak için Microsoft Office 2007 ya da sahip olmalıdır veya sonraki bir sürümünün yüklü veya Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belge oluşturma  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belge oluşturmak için  
  
1.  Yeni bir Microsoft Word belgesi oluşturun.  
  
2.  Aşağıdaki metni yeni bir belgeye yapıştırın:  
  
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
  
3.  İlk satırı "Başlık 1" stili ile biçimlendirin.  
  
4.  Visual Basic kodu içeren satırları seçin. İlk satırı ile başlayan `Imports` anahtar sözcüğü. Son satırı "Bitiş" sınıftır. Courier yazı tipi içeren satırları biçimlendirin. İle yeni bir stil biçimlendirmek ve yeni stil "Code" olarak adlandırın.  
  
5.  Son olarak, çıktı içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.  
  
6.  Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.  
  
    > [!NOTE]
    >  Microsoft Word 2003 kullanıyorsanız seçin **Word 2007 belgesi** içinde **farklı türde Kaydet** aşağı açılan liste.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
