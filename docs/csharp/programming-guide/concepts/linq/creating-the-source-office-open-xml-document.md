---
title: Kaynak Office Open XML belgesi oluşturma (C#)
description: C# öğreticileri ile kullanmak için bir Office Open XML WordprocessingML belgesi oluşturun. Bu makale Microsoft Office gerektirir.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103987"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Open XML belgesi oluşturma (C#)

Bu konu başlığında, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağı gösterilmektedir. Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.

Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.

Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.

## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma

#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturmak için

1. Yeni bir Microsoft Word belgesi oluşturun.

2. Aşağıdaki metni yeni belgeye yapıştırın:

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

3. İlk satırı "Başlık 1" stiliyle biçimlendirin.

4. C# kodunu içeren satırları seçin. İlk satır `using` anahtar sözcüğüyle başlar. Son satır son kapanış ayracı. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.

5. Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.

6. Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.

    > [!NOTE]
    > Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.
