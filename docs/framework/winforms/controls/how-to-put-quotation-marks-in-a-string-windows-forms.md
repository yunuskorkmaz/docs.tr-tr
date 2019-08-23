---
title: 'Nasıl yapılır: Bir dizeye tırnak Işareti koyma (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 20828f75eeae9df33fcc22d8558b26a8a1ab2bdc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910429"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="ebb52-102">Nasıl yapılır: Bir dizeye tırnak Işareti koyma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ebb52-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="ebb52-103">Bazen bir metin dizesinde tırnak işaretleri ("") yerleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebb52-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="ebb52-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ebb52-104">For example:</span></span>  
  
 <span data-ttu-id="ebb52-105">"Bir işleme hak duymuş olursunuz!" diyor</span><span class="sxs-lookup"><span data-stu-id="ebb52-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="ebb52-106">Alternatif olarak, <xref:Microsoft.VisualBasic.ControlChars.Quote> alanı bir sabit olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebb52-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="ebb52-107">Kodunuzda bir dizeye tırnak işareti koymak için</span><span class="sxs-lookup"><span data-stu-id="ebb52-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="ebb52-108">Visual Basic, bir satıra gömülü tırnak işareti olarak iki tırnak işareti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ebb52-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="ebb52-109">Visual C# ve Visual C++' te, kaçış sırasını \\"gömülü tırnak işareti olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ebb52-109">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="ebb52-110">Örneğin, önceki dizeyi oluşturmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebb52-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="ebb52-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="ebb52-111">-or-</span></span>  
  
2. <span data-ttu-id="ebb52-112">Tırnak işareti için ASCII veya Unicode karakteri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ebb52-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="ebb52-113">Visual Basic, ASCII karakterini (34) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebb52-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="ebb52-114">Görselde C#Unicode karakterini kullanın (\u0022).</span><span class="sxs-lookup"><span data-stu-id="ebb52-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    > <span data-ttu-id="ebb52-115">Bu örnekte, temel karakter kümesinde bir karakter atayan bir evrensel karakter adı kullanamadığından, \u0022 kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ebb52-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="ebb52-116">Aksi takdirde, C3851 üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebb52-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="ebb52-117">Daha fazla bilgi için bkz. [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="ebb52-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="ebb52-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="ebb52-118">-or-</span></span>  
  
3. <span data-ttu-id="ebb52-119">Ayrıca karakter için bir sabit tanımlayabilir ve gerektiğinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebb52-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebb52-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebb52-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="ebb52-121">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ebb52-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="ebb52-122">Nasıl yapılır: Windows Forms TextBox denetimindeki ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="ebb52-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="ebb52-123">Nasıl yapılır: Windows Forms TextBox denetimiyle bir parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebb52-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ebb52-124">Nasıl yapılır: Salt okunurdur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebb52-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="ebb52-125">Nasıl yapılır: Windows Forms metin kutusu denetimindeki metni seçme</span><span class="sxs-lookup"><span data-stu-id="ebb52-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ebb52-126">Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satırı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ebb52-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ebb52-127">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="ebb52-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
