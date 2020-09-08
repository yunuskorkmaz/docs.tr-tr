---
title: Kaynak Office Open XML belgesini oluşturma-LINQ to XML
description: Bu öğreticideki diğer örneklerde kullanılan Office Open XML WordprocessingML belgesini oluşturmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552853"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a>Kaynak Office Open XML belgesini oluşturma (LINQ to XML)

Bu makalede, bu öğreticideki diğer örneklerde kullanılan Office Open XML WordprocessingML belgesinin nasıl oluşturulduğu gösterilir. Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.

Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.

Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.

## <a name="create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma

WordprocessingML belgesi oluşturmak için aşağıdaki adımları kullanın:

1. Yeni bir Microsoft Word belgesi oluşturun.
1. Aşağıdaki metni yeni belgeye yapıştırın.
   1. C# için şu metni kullanın:

         ```text
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

   1. Visual Basic için şu metni kullanın:

      ```text
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

1. İlk satırı "Başlık 1" stiliyle biçimlendirin.
1. C# için C# kodunu içeren satırları seçin. İlk satır `using` anahtar sözcüğüyle başlar. Son satır son kapanış ayracı. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.
1. Visual Basic için Visual Basic kodunu içeren satırları seçin. İlk satır `Imports` anahtar sözcüğüyle başlar. Son satır "End Class" dır. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.
1. Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.
1. Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.

> [!NOTE]
> Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)
