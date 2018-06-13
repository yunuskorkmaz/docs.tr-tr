---
title: Kaynak Office Açık XML belge (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: c5884d1e34558d01be4c873c3f44222396e588ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324505"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Açık XML belge (C#) oluşturma
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
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  İlk satırı "Başlık 1" stili ile biçimlendirin.  
  
4.  C# kodu içeren satırları seçin. İlk satırı ile başlayan `using` anahtar sözcüğü. Son kapanış ayracı son satırdır. Courier yazı tipi içeren satırları biçimlendirin. İle yeni bir stil biçimlendirmek ve yeni stil "Code" olarak adlandırın.  
  
5.  Son olarak, çıktı içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.  
  
6.  Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.  
  
    > [!NOTE]
    >  Microsoft Word 2003 kullanıyorsanız seçin **Word 2007 belgesi** içinde **farklı türde Kaydet** aşağı açılan liste.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
