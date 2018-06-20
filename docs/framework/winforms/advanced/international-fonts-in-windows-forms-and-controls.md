---
title: Windows Forms ve denetimlerin uluslararası yazı tipleri
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: b2738f174c9837a2ba83c1306f4617f39ce17de1
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208473"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="57ead-102">Windows Forms ve denetimlerin uluslararası yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="57ead-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="57ead-103">Uluslararası uygulamalarda yazı tipleri seçme önerilen yöntem yazı tipi geri dönüşü mümkün olduğunda kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="57ead-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="57ead-104">Ait ne karakter komut dosyası sistemini belirler yazı tipi geri dönüş anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57ead-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="57ead-105">Yazı tipi geri dönüşü kullanma</span><span class="sxs-lookup"><span data-stu-id="57ead-105">Using font fallback</span></span>

<span data-ttu-id="57ead-106">Bu özelliğin avantajlarından yararlanmak için ayarlamazsanız <xref:System.Drawing.Font> formunuz veya başka bir öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="57ead-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="57ead-107">Uygulama, işletim sisteminin bir yerelleştirilmiş dilden diğerine farklı varsayılan sistem yazı otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="57ead-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="57ead-108">Uygulama çalıştığında, sistem doğru yazı tipi işletim sisteminde seçilen kültür için otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="57ead-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="57ead-109">Yazı tipi stilini değiştirmek için yazı tipi ayarı bulunamadı, kural için bir özel yoktur.</span><span class="sxs-lookup"><span data-stu-id="57ead-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="57ead-110">Bu, kullanıcı bir düğme kalın olarak bir metin kutusundaki metin görünür yapmak için bir uygulama için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="57ead-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="57ead-111">Bunu yapmak için kalın, metin kutusunun yazı tipi stilini değiştirmek için bir işlev ne olursa olsun formun yazı tipi temel alınarak yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="57ead-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="57ead-112">İki yerde bu işlevi çağırmak önemlidir: düğmenin içinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="57ead-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="57ead-113">İşlevi yalnızca çağrıldıysa <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve bazı diğer kod parçası, formun tamamı yazı tipi ailesi değiştirir, metin kutusuna form geri kalanı ile değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="57ead-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

```vb
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
```

```csharp
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

<span data-ttu-id="57ead-114">Ancak, uygulamanızı yerelleştirme sırasında kalın yazı tipiyle kötü belirli diller görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="57ead-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="57ead-115">İlgili bir sorun varsa, normal metne kalın gelen yazı tipini değiştirme seçeneğiniz çevirmenler istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="57ead-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="57ead-116">Çevirmenler genelde geliştiricilerinin değildir ve kaynak kodu erişiminiz yok olduğundan, kaynak dosyaları için yalnızca bu seçenek kaynak dosyalarında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="57ead-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="57ead-117">Bunu yapmak için ayarlamalısınız <xref:System.Drawing.Font.Bold%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="57ead-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="57ead-118">Bu, kaynak dosyaları nerede çevirmenler düzenleyebilirsiniz, yazılmakta yazı tipi ayarı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="57ead-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="57ead-119">Ardından koddan sonra Yazma `InitializeComponent` yazı tipi sıfırlama yöntemi temel ne olursa olsun formun yazı tipi açıktır, ancak kaynak dosyasında belirtilen yazı tipi stilini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="57ead-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="57ead-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57ead-120">See also</span></span>

[<span data-ttu-id="57ead-121">Windows Forms uygulamaları Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="57ead-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)  
[<span data-ttu-id="57ead-122">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="57ead-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)