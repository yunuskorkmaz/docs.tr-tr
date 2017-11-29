---
title: "Windows Formları ve Denetimlerindeki Uluslararası Yazı Tipleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5901113021deffd601b5325ff9a1b8912e74329d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="20f5b-102">Windows Formları ve Denetimlerindeki Uluslararası Yazı Tipleri</span><span class="sxs-lookup"><span data-stu-id="20f5b-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="20f5b-103">Uluslararası uygulamalar yazı tipleri seçme önerilen yöntem yazı tipi geri dönüşü mümkün olduğunda kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="20f5b-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="20f5b-104">Ait ne karakter komut dosyası sistemini belirler yazı tipi geri dönüş anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="20f5b-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="20f5b-105">Yazı tipi geri dönüşü kullanma</span><span class="sxs-lookup"><span data-stu-id="20f5b-105">Using Font Fallback</span></span>  
 <span data-ttu-id="20f5b-106">Bu özelliğin avantajlarından yararlanmak için ayarlamayın <xref:System.Drawing.Font> formunuz veya başka bir öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="20f5b-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="20f5b-107">Uygulama, işletim sisteminin bir yerelleştirilmiş dilden diğerine farklı varsayılan sistem yazı otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="20f5b-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="20f5b-108">Uygulama çalıştığında, sistem doğru yazı tipi işletim sisteminde seçilen kültür için otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20f5b-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="20f5b-109">Yazı tipi stilini değiştirmek için yazı tipi ayarı bulunamadı, kural için bir özel yoktur.</span><span class="sxs-lookup"><span data-stu-id="20f5b-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="20f5b-110">Bu, kullanıcı bir düğme kalın olarak bir metin kutusundaki metin görünür yapmak için bir uygulama için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="20f5b-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="20f5b-111">Bunu yapmak için kalın, metin kutusunun yazı tipi stilini değiştirmek için bir işlev ne olursa olsun formun yazı tipi temel alınarak yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="20f5b-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="20f5b-112">İki yerde bu işlevi çağırmak önemlidir: düğmenin içinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="20f5b-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="20f5b-113">İşlevi yalnızca çağrıldıysa <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve bazı diğer kod parçası, formun tamamı yazı tipi ailesi değiştirir, metin kutusuna form geri kalanı ile değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="20f5b-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 <span data-ttu-id="20f5b-114">Ancak, uygulamanızı yerelleştirme sırasında kalın yazı tipiyle kötü belirli diller görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="20f5b-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="20f5b-115">İlgili bir sorun varsa, normal metne kalın gelen yazı tipini değiştirme seçeneğiniz çevirmenler istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="20f5b-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="20f5b-116">Çevirmenler genelde geliştiricilerinin değildir ve kaynak koduna erişim hakkınız yok olduğundan, kaynak dosyaları için yalnızca bu seçenek kaynak dosyalarında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20f5b-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="20f5b-117">Bunu yapmak için ayarlamalısınız <xref:System.Drawing.Font.Bold%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="20f5b-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="20f5b-118">Bu, kaynak dosyaları nerede çevirmenler düzenleyebilirsiniz, yazılmakta yazı tipi ayarı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="20f5b-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="20f5b-119">Ardından koddan sonra Yazma `InitializeComponent` yazı tipi sıfırlama yöntemi temel ne olursa olsun formun yazı tipi açıktır, ancak kaynak dosyasında belirtilen yazı tipi stilini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="20f5b-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="20f5b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20f5b-120">See Also</span></span>  
 [<span data-ttu-id="20f5b-121">Windows Forms Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="20f5b-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="20f5b-122">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="20f5b-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
