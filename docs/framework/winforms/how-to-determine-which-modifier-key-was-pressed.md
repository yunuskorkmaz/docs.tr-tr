---
title: 'Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 571af49cdf82b876cfb72a7c7636874c8d155fb7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213942"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme
Kullanıcının tuş vuruşları kabul eden bir uygulama oluşturduğunuzda, anahtarları SHIFT, ALT ve CTRL gibi değiştirici tuşları izlemek isteyebilirsiniz. Fare tıklamasına veya diğer anahtarlar ile birlikte bir değiştirici tuşa basıldığında, uygulamanızı uygun şekilde yanıt verebilir. Örneğin, S harfi basıldığında, bu yalnızca "ekranında görünmesini s" neden olabilir, ancak CTRL + S tuşlarını basılı, geçerli belgede kaydedilmemiş olabilir. İşliyorsanız <xref:System.Windows.Forms.Control.KeyDown> olay <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> alınan olayı tarafından hangi değiştirici tuşları basılı işleyici belirtir. Alternatif olarak, <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> da bir bit düzeyinde OR ile birleştirilmiş olarak tüm değiştirici tuşları basılan tuşun karakter belirtir. Ancak, işleniyorsa <xref:System.Windows.Forms.Control.KeyPress> veya bir fare olayın olay işleyicisi, bu bilgileri almaz. Bu durumda, kullanmalısınız <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı. Her iki durumda da, uygun bir bit düzeyinde AND gerçekleştirmelidir <xref:System.Windows.Forms.Keys> ve test ettiğiniz değerleri. <xref:System.Windows.Forms.Keys> Numaralandırma çeşitlemeleri bit gerçekleştirmek önemlidir her değiştirici tuşa ve doğru değerle sunar. Örneğin, SHIFT tuşunu tarafından temsil edilen <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> ve <xref:System.Windows.Forms.Keys.LShiftKey> SHIFT değiştirici tuşa olarak test etmek için doğru değeri <xref:System.Windows.Forms.Keys.Shift>. Benzer şekilde, CTRL ve ALT için değiştiriciler test etmek için kullanması gereken <xref:System.Windows.Forms.Keys.Control> ve <xref:System.Windows.Forms.Keys.Alt> değerler, sırasıyla.  
  
> [!NOTE]
>  Visual Basic programcıları anahtar bilgileri aracılığıyla da erişebilirsiniz <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> özelliği  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Hangi değiştirici tuşa basıldığını belirleme  
  
-   Mü kullanmak `AND` işleciyle <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği ve değerini <xref:System.Windows.Forms.Keys> belirli değiştirici tuşa basıldığını olup olmadığını belirlemek için sabit listesi. Aşağıdaki kod örneği, SHIFT tuşunu basılı içinde olup olmadığını belirlemek gösterilmiştir bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
- [Nasıl yapılır: Visual Basic'te ise CapsLock açıktır belirleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
