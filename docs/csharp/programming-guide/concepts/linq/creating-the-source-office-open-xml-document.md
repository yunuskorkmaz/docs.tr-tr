---
title: Kaynak Office Open XML belgesi (C#) oluşturuluyor
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204159"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Open XML belgesi (C#) oluşturuluyor

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

4. C# Kodu içeren satırları seçin. İlk satır `using` anahtar sözcüğüyle başlar. Son satır son kapanış ayracı. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.

5. Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.

6. Belgeyi kaydedin ve SampleDoc. docx olarak adlandırın.

    > [!NOTE]
    > Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.
