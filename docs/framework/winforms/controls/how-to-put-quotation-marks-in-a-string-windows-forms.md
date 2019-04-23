---
title: 'Nasıl yapılır: (Windows Forms) dizeye tırnak işaretleri koyma'
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
ms.openlocfilehash: 14180f0326b38872f5d1b112c3d9a87022fb79e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328068"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="857b6-102">Nasıl yapılır: (Windows Forms) dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="857b6-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="857b6-103">Bazen tırnak işareti yerleştirmek isteyebilirsiniz ("") içinde bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="857b6-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="857b6-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="857b6-104">For example:</span></span>  
  
 <span data-ttu-id="857b6-105">O söyledi, "Müthiş hak ediyor!"</span><span class="sxs-lookup"><span data-stu-id="857b6-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="857b6-106">Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> alan bir sabit olarak.</span><span class="sxs-lookup"><span data-stu-id="857b6-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="857b6-107">Kodunuzda bir dizedeki tırnak işareti yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="857b6-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="857b6-108">Visual Basic'te, iki tırnak bir satır içine katıştırılmış bir tırnak işareti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="857b6-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="857b6-109">Görselde C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış dizisi Ekle \\"olarak gömülü bir tırnak işareti.</span><span class="sxs-lookup"><span data-stu-id="857b6-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="857b6-110">Örneğin, önceki dize oluşturmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="857b6-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="857b6-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="857b6-111">-or-</span></span>  
  
2. <span data-ttu-id="857b6-112">Tırnak işareti için ASCII veya Unicode karakteri Ekle.</span><span class="sxs-lookup"><span data-stu-id="857b6-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="857b6-113">Visual Basic'te, ASCII karakter (34) kullanın.</span><span class="sxs-lookup"><span data-stu-id="857b6-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="857b6-114">Görselde C#, Unicode karakter (\u0022) kullanın.</span><span class="sxs-lookup"><span data-stu-id="857b6-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="857b6-115">Bu örnekte, bir evrensel karakter adı temel karakter kümesindeki bir karakteri belirler kullanamadığından \u0022 kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="857b6-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="857b6-116">Aksi takdirde, C3851 üretir.</span><span class="sxs-lookup"><span data-stu-id="857b6-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="857b6-117">Daha fazla bilgi için [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="857b6-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="857b6-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="857b6-118">-or-</span></span>  
  
3. <span data-ttu-id="857b6-119">Ayrıca, bir sabit karakter tanımlamak ve kullanmak gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="857b6-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="857b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="857b6-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="857b6-121">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="857b6-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="857b6-122">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme</span><span class="sxs-lookup"><span data-stu-id="857b6-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="857b6-123">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="857b6-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="857b6-124">Nasıl yapılır: Salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="857b6-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="857b6-125">Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç</span><span class="sxs-lookup"><span data-stu-id="857b6-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="857b6-126">Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme</span><span class="sxs-lookup"><span data-stu-id="857b6-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="857b6-127">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="857b6-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
