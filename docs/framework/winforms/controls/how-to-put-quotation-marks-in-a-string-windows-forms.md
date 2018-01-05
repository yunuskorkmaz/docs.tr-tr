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
ms.workload: dotnet
ms.openlocfilehash: 267a69b9470040dfc60f3c0b280b71e3f52dbc88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="fe30f-102">Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fe30f-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="fe30f-103">Bazen tırnak işaretleri yerleştirmeyi isteyebilirsiniz ("") bir metin dizesi içinde.</span><span class="sxs-lookup"><span data-stu-id="fe30f-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="fe30f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fe30f-104">For example:</span></span>  
  
 <span data-ttu-id="fe30f-105">O söyledi, "Müthiş hak!"</span><span class="sxs-lookup"><span data-stu-id="fe30f-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="fe30f-106">Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> bir sabit olarak alan.</span><span class="sxs-lookup"><span data-stu-id="fe30f-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="fe30f-107">Kodunuzu içindeki bir dizeye tırnak işaretleri yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="fe30f-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="fe30f-108">İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], iki tırnak işareti katıştırılmış bir tırnak işareti olarak bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe30f-108">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="fe30f-109">İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış sırası Ekle \\"olarak katıştırılmış bir tırnak işareti.</span><span class="sxs-lookup"><span data-stu-id="fe30f-109">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="fe30f-110">Örneğin, önceki dizesi oluşturmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe30f-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="fe30f-111">veya</span><span class="sxs-lookup"><span data-stu-id="fe30f-111">-or-</span></span>  
  
2.  <span data-ttu-id="fe30f-112">Tırnak işareti ASCII veya Unicode karakteri ekler.</span><span class="sxs-lookup"><span data-stu-id="fe30f-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="fe30f-113">İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ASCII karakter (34) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe30f-113">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], use the ASCII character (34).</span></span> <span data-ttu-id="fe30f-114">İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], Unicode karakter (\u0022) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe30f-114">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="fe30f-115">Bu örnekte, temel karakter kümesinde bir karakter atayan evrensel karakter adları kullanamadığından \u0022 kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fe30f-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="fe30f-116">Aksi takdirde C3851 üretir.</span><span class="sxs-lookup"><span data-stu-id="fe30f-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="fe30f-117">Daha fazla bilgi için bkz: [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="fe30f-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="fe30f-118">veya</span><span class="sxs-lookup"><span data-stu-id="fe30f-118">-or-</span></span>  
  
3.  <span data-ttu-id="fe30f-119">Ayrıca, bir sabit karakter tanımlamak ve kullanmak gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="fe30f-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe30f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe30f-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="fe30f-121">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe30f-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="fe30f-122">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="fe30f-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fe30f-123">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe30f-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fe30f-124">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe30f-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="fe30f-125">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="fe30f-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fe30f-126">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fe30f-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fe30f-127">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="fe30f-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
