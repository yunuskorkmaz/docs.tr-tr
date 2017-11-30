---
title: "Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a4141a27a3b195dbb747a827d2bd9426a948f83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="bd0b7-102">Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bd0b7-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="bd0b7-103">Bazen tırnak işaretleri yerleştirmeyi isteyebilirsiniz ("") bir metin dizesi içinde.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="bd0b7-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bd0b7-104">For example:</span></span>  
  
 <span data-ttu-id="bd0b7-105">O söyledi, "Müthiş hak!"</span><span class="sxs-lookup"><span data-stu-id="bd0b7-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="bd0b7-106">Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> bir sabit olarak alan.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="bd0b7-107">Kodunuzu içindeki bir dizeye tırnak işaretleri yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bd0b7-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="bd0b7-108">İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], iki tırnak işareti katıştırılmış bir tırnak işareti olarak bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-108">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="bd0b7-109">İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış sırası Ekle \\"olarak katıştırılmış bir tırnak işareti.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-109">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="bd0b7-110">Örneğin, önceki dizesi oluşturmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="bd0b7-111">veya</span><span class="sxs-lookup"><span data-stu-id="bd0b7-111">-or-</span></span>  
  
2.  <span data-ttu-id="bd0b7-112">Tırnak işareti ASCII veya Unicode karakteri ekler.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="bd0b7-113">İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ASCII karakter (34) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-113">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], use the ASCII character (34).</span></span> <span data-ttu-id="bd0b7-114">İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], Unicode karakter (\u0022) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-114">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bd0b7-115">Bu örnekte, temel karakter kümesinde bir karakter atayan evrensel karakter adları kullanamadığından \u0022 kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="bd0b7-116">Aksi takdirde C3851 üretir.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="bd0b7-117">Daha fazla bilgi için bkz: [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="bd0b7-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="bd0b7-118">veya</span><span class="sxs-lookup"><span data-stu-id="bd0b7-118">-or-</span></span>  
  
3.  <span data-ttu-id="bd0b7-119">Ayrıca, bir sabit karakter tanımlamak ve kullanmak gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bd0b7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd0b7-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="bd0b7-121">TextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="bd0b7-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="bd0b7-122">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="bd0b7-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="bd0b7-123">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd0b7-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="bd0b7-124">Nasıl yapılır: salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd0b7-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="bd0b7-125">Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde</span><span class="sxs-lookup"><span data-stu-id="bd0b7-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="bd0b7-126">Nasıl yapılır: birden çok satır Windows Forms TextBox denetiminde görünümü</span><span class="sxs-lookup"><span data-stu-id="bd0b7-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="bd0b7-127">TextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="bd0b7-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
