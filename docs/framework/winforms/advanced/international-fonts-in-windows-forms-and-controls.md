---
title: Formlarda ve denetimlerde uluslararası yazı tipleri
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
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743512"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="7ec4d-102">Windows Forms ve denetimlerinde uluslararası yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="7ec4d-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="7ec4d-103">Uluslararası uygulamalarda, yazı tipi seçme önerilen yöntemi, mümkün olan yerlerde yazı tipi geri dönüşü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="7ec4d-104">Yazı tipi geri dönüş, sistemin karakterin ait olduğu betiği belirlediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="7ec4d-105">Yazı tipi geri dönüşü kullanma</span><span class="sxs-lookup"><span data-stu-id="7ec4d-105">Using font fallback</span></span>

<span data-ttu-id="7ec4d-106">Bu özellikten yararlanmak için formunuzun veya başka bir öğenin <xref:System.Drawing.Font> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="7ec4d-107">Uygulama otomatik olarak varsayılan sistem yazı tipini kullanır ve bu, işletim sisteminin yerelleştirilmiş bir dilinden diğerine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="7ec4d-108">Uygulama çalıştığında, sistem otomatik olarak işletim sisteminde seçilen kültür için doğru yazı tipini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="7ec4d-109">Yazı tipi stilini değiştirmek için olan, yazı tipini ayarlamamayan kural için bir özel durum vardır.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="7ec4d-110">Bu, kullanıcının metin kutusunda metin kalın yazı altında görünmesini sağlamak için bir düğmeye tıkladığı bir uygulama için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="7ec4d-111">Bunu yapmak için, form yazı tipinin ne olursa olsun metin kutusunun yazı tipi stilini kalın olarak değiştirmek için bir işlev yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="7ec4d-112">Bu işlevi iki yerde çağırmak önemlidir: düğmenin <xref:System.Windows.Forms.Control.Click> olay işleyicisinde ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisinde.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="7ec4d-113">İşlev yalnızca <xref:System.Windows.Forms.Control.Click> olay işleyicisinde çağrılırsa ve diğer kod parçaları formun tamamının yazı tipi ailesini değiştirirse, metin kutusu formun geri kalanı ile değişmez.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="7ec4d-114">Ancak, uygulamanızı yerelleştirmeniz durumunda, kalın yazı tipi belirli diller için kötü bir şekilde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="7ec4d-115">Bu sorun varsa, Yereller için yazı tipini kalın iken normal metne değiştirme seçeneğine sahip olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="7ec4d-116">Yerellerin genellikle geliştiriciler olmadığından ve kaynak koda erişimi olmadığından, bu seçeneğin kaynak dosyalarında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="7ec4d-117">Bunu yapmak için <xref:System.Drawing.Font.Bold%2A> özelliğini `true`olarak ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="7ec4d-118">Bu, yazı tipi ayarının, Yerelleştiricilerin düzenleyebileceği kaynak dosyalara yazıldığı şekilde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="7ec4d-119">Daha sonra, form yazı tipine göre yazı tipini sıfırlamak için `InitializeComponent` yönteminden sonra kodu yazarsınız, ancak kaynak dosyasında belirtilen yazı tipi stilini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="7ec4d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-120">See also</span></span>

- [<span data-ttu-id="7ec4d-121">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="7ec4d-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
