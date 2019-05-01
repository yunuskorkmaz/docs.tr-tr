---
title: Windows formlar ve denetimler uluslararası yazı tipleri
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
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942902"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="10a0b-102">Windows formlar ve denetimler uluslararası yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="10a0b-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="10a0b-103">Uluslararası uygulamalar, yazı tiplerini seçme önerilen yöntem yazı tipi geri dönüşü mümkünse kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="10a0b-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="10a0b-104">Ait neler karakterle betik sistemi belirler yazı tipi geri dönüş anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="10a0b-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="10a0b-105">Yazı tipi geri dönüş kullanma</span><span class="sxs-lookup"><span data-stu-id="10a0b-105">Using font fallback</span></span>

<span data-ttu-id="10a0b-106">Bu özelliğin avantajlarından yararlanmak için ayarlamamanız <xref:System.Drawing.Font> formunuza veya başka bir öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="10a0b-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="10a0b-107">Uygulama, işletim sisteminin bir yerelleştirilmiş dilden diğerine farklılık gösterir. varsayılan sistem yazı otomatik olarak kullanacak.</span><span class="sxs-lookup"><span data-stu-id="10a0b-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="10a0b-108">Uygulama çalışırken, sistemin doğru yazı tipi işletim sisteminin seçili kültür için otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10a0b-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="10a0b-109">Yazı tipi stilini değiştirmek için yazı tipi ayarlanmaması, kural için bir özel yoktur.</span><span class="sxs-lookup"><span data-stu-id="10a0b-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="10a0b-110">Bu, kullanıcı kalın yazı tipinde metin kutusunda metnin görünmesini sağlamak için bir düğmeye tıkladığında bir uygulama için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="10a0b-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="10a0b-111">Bunu yapmak için hangi formun yazı tipi bağlı kalın için metin kutusunun yazı tipi stilini değiştirmek için bir işlev yazmalısınız.</span><span class="sxs-lookup"><span data-stu-id="10a0b-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="10a0b-112">İki yerde bu işlevi çağırmak önemlidir: düğmenin içinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="10a0b-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="10a0b-113">İşlev çağrılırsa yalnızca <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve bazı bir kod parçası, formun tamamını yazı tipi ailesini değiştirir, metin kutusuna form geri kalanı ile değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="10a0b-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="10a0b-114">Ancak, uygulamanız yerelleştirdiğiniz zaman kalın yazı tipiyle kötü performans gösteren bazı diller görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="10a0b-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="10a0b-115">Bu önemliyse, çevirmenlerin normal metin yazı tipinin kalın'ndan geçiş yapma seçeneğine sahip olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="10a0b-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="10a0b-116">Yerelleştiriciler genellikle geliştiriciler değildir ve kaynak koduna erişiminiz yoksa bu yana, yalnızca kaynak dosyaları için bu seçeneği kaynak dosyalarında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10a0b-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="10a0b-117">Bunu yapmak için ayarlarsınız <xref:System.Drawing.Font.Bold%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="10a0b-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="10a0b-118">Kaynak dosyaları nerede yerelleştiriciler düzenleyebilirsiniz, yazılan yazı tipi ayarlarını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="10a0b-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="10a0b-119">Ardından sonra kodu yazdığınız `InitializeComponent` yazı sıfırlamak için gereken yöntemini temel ne olursa olsun formun yazı tipi açıktır, ancak kaynak dosyasında belirtilen yazı tipi stili kullanarak.</span><span class="sxs-lookup"><span data-stu-id="10a0b-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="10a0b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10a0b-120">See also</span></span>

- [<span data-ttu-id="10a0b-121">Windows Forms uygulamaları Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="10a0b-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
- [<span data-ttu-id="10a0b-122">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="10a0b-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)
