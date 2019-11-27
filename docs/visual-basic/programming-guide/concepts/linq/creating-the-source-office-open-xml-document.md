---
title: Kaynak Office Open XML Belgesi Oluşturma
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 5f7a9baebd2d1db73ab17924e0ff8a7408637ee8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346413"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="b49be-102">Kaynak Office Open XML belgesi (Visual Basic) oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="b49be-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="b49be-103">Bu konu başlığında, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b49be-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="b49be-104">Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b49be-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="b49be-105">Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="b49be-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="b49be-106">Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b49be-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="b49be-107">WordprocessingML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b49be-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="b49be-108">WordprocessingML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b49be-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="b49be-109">Yeni bir Microsoft Word belgesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b49be-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="b49be-110">Aşağıdaki metni yeni belgeye yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="b49be-110">Paste the following text into the new document:</span></span>  
  
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
  
3. <span data-ttu-id="b49be-111">İlk satırı "Başlık 1" stiliyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b49be-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="b49be-112">Visual Basic kodunu içeren satırları seçin.</span><span class="sxs-lookup"><span data-stu-id="b49be-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="b49be-113">İlk satır `Imports` anahtar sözcüğüyle başlar.</span><span class="sxs-lookup"><span data-stu-id="b49be-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="b49be-114">Son satır "End Class" dır.</span><span class="sxs-lookup"><span data-stu-id="b49be-114">The last line is "End Class".</span></span> <span data-ttu-id="b49be-115">Çizgileri Courier yazı tipiyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b49be-115">Format the lines with the courier font.</span></span> <span data-ttu-id="b49be-116">Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b49be-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="b49be-117">Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stiliyle biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b49be-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="b49be-118">Belgeyi kaydedin ve SampleDoc. docx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b49be-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b49be-119">Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="b49be-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49be-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b49be-120">See also</span></span>

- [<span data-ttu-id="b49be-121">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b49be-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
