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
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="d0324-102">Kaynak Office Açık XML Belgesioluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="d0324-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="d0324-103">Bu konu, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0324-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="d0324-104">Bu yönergeleri izlerseniz, çıktınız her örnekte sağlanan çıktıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="d0324-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="d0324-105">Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0324-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="d0324-106">Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya daha sonra yüklü olması veya Microsoft Office 2003'e Word, Excel ve PowerPoint 2007 Dosya Biçimleri için Microsoft Office Uyumluluk Paketi'ne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0324-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="d0324-107">WordprocessingML Belgesioluşturma</span><span class="sxs-lookup"><span data-stu-id="d0324-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="d0324-108">WordprocessingML belgesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d0324-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="d0324-109">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0324-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="d0324-110">Aşağıdaki metni yeni belgeye yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="d0324-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="d0324-111">İlk satırı "Başlık 1" stiliyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="d0324-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="d0324-112">C# kodunu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="d0324-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="d0324-113">İlk satır `using` anahtar kelime ile başlar.</span><span class="sxs-lookup"><span data-stu-id="d0324-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="d0324-114">Son satır son kapanış ayraçtır.</span><span class="sxs-lookup"><span data-stu-id="d0324-114">The last line is the last closing brace.</span></span> <span data-ttu-id="d0324-115">Satırları kurye yazı tipiyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="d0324-115">Format the lines with the courier font.</span></span> <span data-ttu-id="d0324-116">Bunları yeni bir stille biçimlendirin ve yeni stili "Kod" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d0324-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="d0324-117">Son olarak, çıktıiçeren tüm satırı seçin ve `Code` stil ile biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="d0324-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="d0324-118">Belgeyi kaydedin ve sampledoc.docx adını verin.</span><span class="sxs-lookup"><span data-stu-id="d0324-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0324-119">Microsoft Word 2003 kullanıyorsanız, Tür açılır listesinde **Kaydet'te** **Word 2007 Belgesi'ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="d0324-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
