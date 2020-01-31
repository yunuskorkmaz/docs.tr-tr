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
# <a name="international-fonts-in-windows-forms-and-controls"></a>Windows Forms ve denetimlerinde uluslararası yazı tipleri

Uluslararası uygulamalarda, yazı tipi seçme önerilen yöntemi, mümkün olan yerlerde yazı tipi geri dönüşü kullanmaktır. Yazı tipi geri dönüş, sistemin karakterin ait olduğu betiği belirlediği anlamına gelir.

## <a name="using-font-fallback"></a>Yazı tipi geri dönüşü kullanma

Bu özellikten yararlanmak için formunuzun veya başka bir öğenin <xref:System.Drawing.Font> özelliğini ayarlayın. Uygulama otomatik olarak varsayılan sistem yazı tipini kullanır ve bu, işletim sisteminin yerelleştirilmiş bir dilinden diğerine göre farklılık gösterir. Uygulama çalıştığında, sistem otomatik olarak işletim sisteminde seçilen kültür için doğru yazı tipini sağlar.

Yazı tipi stilini değiştirmek için olan, yazı tipini ayarlamamayan kural için bir özel durum vardır. Bu, kullanıcının metin kutusunda metin kalın yazı altında görünmesini sağlamak için bir düğmeye tıkladığı bir uygulama için önemli olabilir. Bunu yapmak için, form yazı tipinin ne olursa olsun metin kutusunun yazı tipi stilini kalın olarak değiştirmek için bir işlev yazarsınız. Bu işlevi iki yerde çağırmak önemlidir: düğmenin <xref:System.Windows.Forms.Control.Click> olay işleyicisinde ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisinde. İşlev yalnızca <xref:System.Windows.Forms.Control.Click> olay işleyicisinde çağrılırsa ve diğer kod parçaları formun tamamının yazı tipi ailesini değiştirirse, metin kutusu formun geri kalanı ile değişmez.

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

Ancak, uygulamanızı yerelleştirmeniz durumunda, kalın yazı tipi belirli diller için kötü bir şekilde görüntülenebilir. Bu sorun varsa, Yereller için yazı tipini kalın iken normal metne değiştirme seçeneğine sahip olmak istersiniz. Yerellerin genellikle geliştiriciler olmadığından ve kaynak koda erişimi olmadığından, bu seçeneğin kaynak dosyalarında ayarlanması gerekir. Bunu yapmak için <xref:System.Drawing.Font.Bold%2A> özelliğini `true`olarak ayarlarsınız. Bu, yazı tipi ayarının, Yerelleştiricilerin düzenleyebileceği kaynak dosyalara yazıldığı şekilde sonuçlanır. Daha sonra, form yazı tipine göre yazı tipini sıfırlamak için `InitializeComponent` yönteminden sonra kodu yazarsınız, ancak kaynak dosyasında belirtilen yazı tipi stilini kullanarak.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
