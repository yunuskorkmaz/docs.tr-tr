---
title: Kaynak Office Open XML belgesi (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 7941864e5dc2401a27df151c8c7806218609fcd4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558239"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Open XML belgesi (C#) oluşturma
Bu konu, diğer bu öğreticideki örneklerde Office Open XML WordprocessingML belgesi nasıl oluşturacağınızı gösterir. Bu yönergeleri izleyin, çıkış her örnekte sağlanan çıkış eşleşir.  
  
 Ancak, bu öğreticideki örneklerde, geçerli bir WordprocessingML belgesi ile çalışır.  
  
 Bu öğreticide bir belge oluşturmak için ya da Microsoft Office 2007 yüklü olmalıdır veya sonraki bir sürümünün yüklü veya Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturmak için  
  
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
  
3.  İlk satır stili "Başlık 1" ile biçimlendirin.  
  
4.  C# kodu içeren satırları seçin. İlk satırı ile başlayan `using` anahtar sözcüğü. Son satır son kapanış ayracından değil. Satırları courier yazı biçimi. İle yeni bir stil biçimlendirir ve yeni stil "Code" olarak adlandırın.  
  
5.  Son olarak, çıktısını içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.  
  
6.  Belgeyi kaydedin ve SampleDoc.docx adlandırın.  
  
    > [!NOTE]
    >  Microsoft Word 2003 kullanıyorsanız **Word 2007 belgesi** içinde **farklı kaydetme türü** aşağı açılan listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Öğretici: WordprocessingML belgesindeki (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
