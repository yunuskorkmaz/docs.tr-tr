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
# <a name="international-fonts-in-windows-forms-and-controls"></a>Windows formlar ve denetimler uluslararası yazı tipleri

Uluslararası uygulamalar, yazı tiplerini seçme önerilen yöntem yazı tipi geri dönüşü mümkünse kullanmaktır. Ait neler karakterle betik sistemi belirler yazı tipi geri dönüş anlamına gelir.

## <a name="using-font-fallback"></a>Yazı tipi geri dönüş kullanma

Bu özelliğin avantajlarından yararlanmak için ayarlamamanız <xref:System.Drawing.Font> formunuza veya başka bir öğenin özellik. Uygulama, işletim sisteminin bir yerelleştirilmiş dilden diğerine farklılık gösterir. varsayılan sistem yazı otomatik olarak kullanacak. Uygulama çalışırken, sistemin doğru yazı tipi işletim sisteminin seçili kültür için otomatik olarak sağlar.

Yazı tipi stilini değiştirmek için yazı tipi ayarlanmaması, kural için bir özel yoktur. Bu, kullanıcı kalın yazı tipinde metin kutusunda metnin görünmesini sağlamak için bir düğmeye tıkladığında bir uygulama için önemli olabilir. Bunu yapmak için hangi formun yazı tipi bağlı kalın için metin kutusunun yazı tipi stilini değiştirmek için bir işlev yazmalısınız. İki yerde bu işlevi çağırmak önemlidir: düğmenin içinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve <xref:System.Windows.Forms.Control.FontChanged> olay işleyicisi. İşlev çağrılırsa yalnızca <xref:System.Windows.Forms.Control.Click> olay işleyicisi ve bazı bir kod parçası, formun tamamını yazı tipi ailesini değiştirir, metin kutusuna form geri kalanı ile değiştirmez.

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

Ancak, uygulamanız yerelleştirdiğiniz zaman kalın yazı tipiyle kötü performans gösteren bazı diller görüntüleyebilir. Bu önemliyse, çevirmenlerin normal metin yazı tipinin kalın'ndan geçiş yapma seçeneğine sahip olmasını istediğiniz. Yerelleştiriciler genellikle geliştiriciler değildir ve kaynak koduna erişiminiz yoksa bu yana, yalnızca kaynak dosyaları için bu seçeneği kaynak dosyalarında ayarlanması gerekir. Bunu yapmak için ayarlarsınız <xref:System.Drawing.Font.Bold%2A> özelliğini `true`. Kaynak dosyaları nerede yerelleştiriciler düzenleyebilirsiniz, yazılan yazı tipi ayarlarını sonuçlanır. Ardından sonra kodu yazdığınız `InitializeComponent` yazı sıfırlamak için gereken yöntemini temel ne olursa olsun formun yazı tipi açıktır, ancak kaynak dosyasında belirtilen yazı tipi stili kullanarak.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms uygulamaları Genelleştirme](globalizing-windows-forms.md)
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
