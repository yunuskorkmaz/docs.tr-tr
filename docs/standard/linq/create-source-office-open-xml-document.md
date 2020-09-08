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
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="eb005-103">Kaynak Office Open XML belgesini oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="eb005-103">Create the source Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="eb005-104">Bu makalede, bu öğreticideki diğer örneklerde kullanılan Office Open XML WordprocessingML belgesinin nasıl oluşturulduğu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb005-104">This article shows how to create the Office Open XML WordprocessingML document used by the other examples in this tutorial.</span></span> <span data-ttu-id="eb005-105">Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="eb005-105">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="eb005-106">Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb005-106">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="eb005-107">Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb005-107">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="create-the-wordprocessingml-document"></a><span data-ttu-id="eb005-108">WordprocessingML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb005-108">Create the WordprocessingML document</span></span>

<span data-ttu-id="eb005-109">WordprocessingML belgesi oluşturmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb005-109">Use the following steps to create the WordprocessingML document:</span></span>

1. <span data-ttu-id="eb005-110">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb005-110">Create a new Microsoft Word document.</span></span>
1. <span data-ttu-id="eb005-111">Aşağıdaki metni yeni belgeye yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb005-111">Paste the following text into the new document.</span></span>
   1. <span data-ttu-id="eb005-112">C# için şu metni kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb005-112">For C#, use this text:</span></span>

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

   1. <span data-ttu-id="eb005-113">Visual Basic için şu metni kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb005-113">For Visual Basic, use this text:</span></span>

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

1. <span data-ttu-id="eb005-114">İlk satırı "Başlık 1" stiliyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="eb005-114">Format the first line with the style "Heading 1".</span></span>
1. <span data-ttu-id="eb005-115">C# için C# kodunu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="eb005-115">For C#, select the lines that contain the C# code.</span></span> <span data-ttu-id="eb005-116">İlk satır `using` anahtar sözcüğüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="eb005-116">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="eb005-117">Son satır son kapanış ayracı.</span><span class="sxs-lookup"><span data-stu-id="eb005-117">The last line is the last closing brace.</span></span> <span data-ttu-id="eb005-118">Çizgileri Courier yazı tipiyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="eb005-118">Format the lines with the courier font.</span></span> <span data-ttu-id="eb005-119">Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eb005-119">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="eb005-120">Visual Basic için Visual Basic kodunu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="eb005-120">For Visual Basic, select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="eb005-121">İlk satır `Imports` anahtar sözcüğüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="eb005-121">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="eb005-122">Son satır "End Class" dır.</span><span class="sxs-lookup"><span data-stu-id="eb005-122">The last line is "End Class".</span></span> <span data-ttu-id="eb005-123">Çizgileri Courier yazı tipiyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="eb005-123">Format the lines with the courier font.</span></span> <span data-ttu-id="eb005-124">Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eb005-124">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="eb005-125">Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="eb005-125">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>
1. <span data-ttu-id="eb005-126">Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eb005-126">Save the document, and name it SampleDoc.docx.</span></span>

> [!NOTE]
> <span data-ttu-id="eb005-127">Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="eb005-127">If you're using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb005-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb005-128">See also</span></span>

- [<span data-ttu-id="eb005-129">Öğretici: WordprocessingML belgesinde içerik Işleme</span><span class="sxs-lookup"><span data-stu-id="eb005-129">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
