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
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="c85bb-102">Kaynak Office Open XML belgesi (C#) oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="c85bb-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="c85bb-103">Bu konu başlığında, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c85bb-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="c85bb-104">Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c85bb-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="c85bb-105">Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="c85bb-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="c85bb-106">Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c85bb-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="c85bb-107">WordprocessingML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c85bb-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="c85bb-108">WordprocessingML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c85bb-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="c85bb-109">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c85bb-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="c85bb-110">Aşağıdaki metni yeni belgeye yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="c85bb-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="c85bb-111">İlk satırı "Başlık 1" stiliyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="c85bb-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="c85bb-112">C# Kodu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="c85bb-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="c85bb-113">İlk satır `using` anahtar sözcüğüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="c85bb-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="c85bb-114">Son satır son kapanış ayracı.</span><span class="sxs-lookup"><span data-stu-id="c85bb-114">The last line is the last closing brace.</span></span> <span data-ttu-id="c85bb-115">Çizgileri Courier yazı tipiyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="c85bb-115">Format the lines with the courier font.</span></span> <span data-ttu-id="c85bb-116">Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c85bb-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="c85bb-117">Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="c85bb-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="c85bb-118">Belgeyi kaydedin ve SampleDoc. docx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c85bb-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c85bb-119">Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="c85bb-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
