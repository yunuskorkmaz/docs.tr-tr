---
title: Kaynak Office Açık XML Belgesioluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204159"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Kaynak Office Açık XML Belgesioluşturma (C#)

Bu konu, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağımı gösterir. Bu yönergeleri izlerseniz, çıktınız her örnekte sağlanan çıktıyla eşleşir.

Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışır.

Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya daha sonra yüklü olması veya Microsoft Office 2003'e Word, Excel ve PowerPoint 2007 Dosya Biçimleri için Microsoft Office Uyumluluk Paketi'ne sahip olması gerekir.

## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML Belgesioluşturma

#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesini oluşturmak için

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

4. C# kodunu içeren satırları seçin. İlk satır `using` anahtar kelime ile başlar. Son satır son kapanış ayraçtır. Satırları kurye yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni stili "Kod" olarak adlandırın.

5. Son olarak, çıktıiçeren tüm satırı seçin ve `Code` stil ile biçimlendirin.

6. Belgeyi kaydedin ve sampledoc.docx adını verin.

    > [!NOTE]
    > Microsoft Word 2003 kullanıyorsanız, Tür açılır listesinde **Kaydet'te** **Word 2007 Belgesi'ni** seçin.
