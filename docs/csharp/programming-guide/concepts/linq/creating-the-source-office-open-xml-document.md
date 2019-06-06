---
title: Kaynak Office Open XML belgesi (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 024b6c80cdedf38fd2dcee77562c0105df7bd033
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690100"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="56381-102">Kaynak Office Open XML belgesi (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="56381-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="56381-103">Bu konu, diğer bu öğreticideki örneklerde Office Open XML WordprocessingML belgesi nasıl oluşturacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="56381-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="56381-104">Bu yönergeleri izleyin, çıkış her örnekte sağlanan çıkış eşleşir.</span><span class="sxs-lookup"><span data-stu-id="56381-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="56381-105">Ancak, bu öğreticideki örneklerde, geçerli bir WordprocessingML belgesi ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="56381-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="56381-106">Bu öğreticide bir belge oluşturmak için ya da Microsoft Office 2007 yüklü olmalıdır veya sonraki bir sürümünün yüklü veya Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56381-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="56381-107">WordprocessingML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="56381-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="56381-108">WordprocessingML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="56381-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="56381-109">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="56381-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="56381-110">Aşağıdaki metni yeni bir belgeye yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="56381-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="56381-111">İlk satır stili "Başlık 1" ile biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="56381-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="56381-112">C# kodu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="56381-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="56381-113">İlk satırı ile başlayan `using` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="56381-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="56381-114">Son satır son kapanış ayracından değil.</span><span class="sxs-lookup"><span data-stu-id="56381-114">The last line is the last closing brace.</span></span> <span data-ttu-id="56381-115">Satırları courier yazı biçimi.</span><span class="sxs-lookup"><span data-stu-id="56381-115">Format the lines with the courier font.</span></span> <span data-ttu-id="56381-116">İle yeni bir stil biçimlendirir ve yeni stil "Code" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="56381-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="56381-117">Son olarak, çıktısını içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.</span><span class="sxs-lookup"><span data-stu-id="56381-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="56381-118">Belgeyi kaydedin ve SampleDoc.docx adlandırın.</span><span class="sxs-lookup"><span data-stu-id="56381-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56381-119">Microsoft Word 2003 kullanıyorsanız **Word 2007 belgesi** içinde **farklı kaydetme türü** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="56381-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
