---
title: Kaynak Office Open XML belgesi (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 8b36d119eb2da7445649b8db1132b7deea2c684c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322400"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Open XML belgesi (C#) oluşturma
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
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. İlk satır stili "Başlık 1" ile biçimlendirin.  
  
4. C# kodu içeren satırları seçin. İlk satırı ile başlayan `using` anahtar sözcüğü. Son satır son kapanış ayracından değil. Satırları courier yazı biçimi. İle yeni bir stil biçimlendirir ve yeni stil "Code" olarak adlandırın.  
  
5. Son olarak, çıktısını içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.  
  
6. Belgeyi kaydedin ve SampleDoc.docx adlandırın.  
  
    > [!NOTE]
    >  Microsoft Word 2003 kullanıyorsanız **Word 2007 belgesi** içinde **farklı kaydetme türü** aşağı açılan listesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki içeriği düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
