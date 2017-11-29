---
title: "Kaynak Office Açık XML belge (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c573f703ea3d7550dabd994f538e28e197874715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="348e7-102">Kaynak Office Açık XML belge (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="348e7-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="348e7-103">Bu konu diğer örnekleri Bu öğreticide kullanmak Office Açık XML WordprocessingML belgesi nasıl oluşturacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="348e7-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="348e7-104">Bu yönergeleri izleyin, her örnekte sağlanan çıkış, çıktı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="348e7-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="348e7-105">Ancak, Bu öğretici örneklerde sahip herhangi bir geçerli WordprocessingML belgeyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="348e7-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="348e7-106">Bu öğretici kullanır belge oluşturmak için Microsoft Office 2007 ya da sahip olmalıdır veya sonraki bir sürümünün yüklü veya Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="348e7-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="348e7-107">WordprocessingML belge oluşturma</span><span class="sxs-lookup"><span data-stu-id="348e7-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="348e7-108">WordprocessingML belge oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="348e7-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="348e7-109">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="348e7-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="348e7-110">Aşağıdaki metni yeni bir belgeye yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="348e7-110">Paste the following text into the new document:</span></span>  
  
    ```  
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
  
3.  <span data-ttu-id="348e7-111">İlk satırı "Başlık 1" stili ile biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="348e7-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="348e7-112">Visual Basic kodu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="348e7-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="348e7-113">İlk satırı ile başlayan `Imports` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="348e7-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="348e7-114">Son satırı "Bitiş" sınıftır.</span><span class="sxs-lookup"><span data-stu-id="348e7-114">The last line is "End Class".</span></span> <span data-ttu-id="348e7-115">Courier yazı tipi içeren satırları biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="348e7-115">Format the lines with the courier font.</span></span> <span data-ttu-id="348e7-116">İle yeni bir stil biçimlendirmek ve yeni stil "Code" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="348e7-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="348e7-117">Son olarak, çıktı içeren tüm satırı seçin ve ile biçimlendirmeniz `Code` stili.</span><span class="sxs-lookup"><span data-stu-id="348e7-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="348e7-118">Belgeyi kaydedin ve SampleDoc.docx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="348e7-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="348e7-119">Microsoft Word 2003 kullanıyorsanız seçin **Word 2007 belgesi** içinde **farklı türde Kaydet** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="348e7-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348e7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="348e7-120">See Also</span></span>  
 [<span data-ttu-id="348e7-121">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="348e7-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
