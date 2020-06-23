---
title: 'Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma'
description: Bir metin dizesine tırnak işareti yerleştirmeyi öğrenin. Ayrıca, quote alanını bir sabit olarak kullanmayı öğrenin.
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
ms.openlocfilehash: 08a3e2ab5662cbbf7825890ab430fddcd7b4a9ce
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903629"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="29422-104">Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="29422-104">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="29422-105">Bazen bir metin dizesinde tırnak işaretleri ("") yerleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29422-105">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="29422-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="29422-106">For example:</span></span>  
  
 <span data-ttu-id="29422-107">"Bir işleme hak duymuş olursunuz!" diyor</span><span class="sxs-lookup"><span data-stu-id="29422-107">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="29422-108">Alternatif olarak, <xref:Microsoft.VisualBasic.ControlChars.Quote> alanı bir sabit olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29422-108">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="29422-109">Kodunuzda bir dizeye tırnak işareti koymak için</span><span class="sxs-lookup"><span data-stu-id="29422-109">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="29422-110">Visual Basic, bir satıra gömülü tırnak işareti olarak iki tırnak işareti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29422-110">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="29422-111">Visual C# ve Visual C++, kaçış sırasını \\ "katıştırılmış tırnak işareti olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29422-111">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="29422-112">Örneğin, önceki dizeyi oluşturmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="29422-112">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="29422-113">-veya-</span><span class="sxs-lookup"><span data-stu-id="29422-113">-or-</span></span>  
  
2. <span data-ttu-id="29422-114">Tırnak işareti için ASCII veya Unicode karakteri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29422-114">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="29422-115">Visual Basic, ASCII karakterini (34) kullanın.</span><span class="sxs-lookup"><span data-stu-id="29422-115">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="29422-116">Visual C# ' de Unicode karakterini (\u0022) kullanın.</span><span class="sxs-lookup"><span data-stu-id="29422-116">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    > <span data-ttu-id="29422-117">Bu örnekte, temel karakter kümesinde bir karakter atayan bir evrensel karakter adı kullanamadığından, \u0022 kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="29422-117">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="29422-118">Aksi takdirde, C3851 üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29422-118">Otherwise, you produce C3851.</span></span> <span data-ttu-id="29422-119">Daha fazla bilgi için bkz. [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="29422-119">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="29422-120">-veya-</span><span class="sxs-lookup"><span data-stu-id="29422-120">-or-</span></span>  
  
3. <span data-ttu-id="29422-121">Ayrıca karakter için bir sabit tanımlayabilir ve gerektiğinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29422-121">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29422-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29422-122">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="29422-123">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="29422-123">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="29422-124">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="29422-124">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="29422-125">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29422-125">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="29422-126">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29422-126">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="29422-127">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="29422-127">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="29422-128">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="29422-128">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="29422-129">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="29422-129">TextBox Control</span></span>](textbox-control-windows-forms.md)
