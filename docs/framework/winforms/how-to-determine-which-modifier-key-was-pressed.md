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
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964320"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme
Kullanıcının tuş vuruşlarını kabul eden bir uygulama oluşturduğunuzda, SHIFT, ALT ve CTRL tuşları gibi değiştirici tuşları izlemek de isteyebilirsiniz. Değiştirici tuşa diğer anahtarlarla birlikte basıldığında veya fare tıklamasıyla, uygulamanız uygun şekilde yanıt verebilir. Örneğin, S harfi basılıysa bu, ekranda "S" görünmesine neden olabilir, ancak CTRL + S tuşlarına basıldığında geçerli belge kaydedilebilir. <xref:System.Windows.Forms.Control.KeyDown> Olayı işleyiniz <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> , olay işleyicisi tarafından <xref:System.Windows.Forms.KeyEventArgs> alınan öğesinin özelliği hangi değiştirici tuşlarına basılanı belirtir. Alternatif olarak, <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> <xref:System.Windows.Forms.KeyEventArgs> özelliği, basılan karakteri ve bit düzeyinde OR ile Birleşik değiştirici anahtarlarını belirtir. Ancak, <xref:System.Windows.Forms.Control.KeyPress> olayı veya bir fare olayını işliyorsa, olay işleyicisi bu bilgileri almaz. Bu durumda, <xref:System.Windows.Forms.Control.ModifierKeys%2A> <xref:System.Windows.Forms.Control> sınıfının özelliğini kullanmanız gerekir. Her iki durumda da, uygun <xref:System.Windows.Forms.Keys> değeri ve test ettiğiniz değeri bir bit düzeyinde ve yapmanız gerekir. <xref:System.Windows.Forms.Keys> Sabit listesi her bir değiştirici anahtarın varyasyonlarını sunar, bu nedenle bit düzeyinde ve doğru değerle birlikte yapmanız önemlidir. Örneğin, <xref:System.Windows.Forms.Keys.Shift>SHIFT tuşu <xref:System.Windows.Forms.Keys.ShiftKey>,, <xref:System.Windows.Forms.Keys.LShiftKey> <xref:System.Windows.Forms.Keys.Shift>ve değiştirici anahtar olarak SHIFT 'i test etmek için doğru değer ile temsil edilir. <xref:System.Windows.Forms.Keys.RShiftKey> Benzer şekilde, CTRL ve alt tuşlarını değiştiriciler olarak test etmek için sırasıyla <xref:System.Windows.Forms.Keys.Control> ve <xref:System.Windows.Forms.Keys.Alt> değerlerini kullanmanız gerekir.  
  
> [!NOTE]
> Visual Basic programcılar, <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> özelliği aracılığıyla anahtar bilgilerine de erişebilir  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Hangi değiştirici tuşa basıldığını belirleme  
  
- Belirli bir değiştirici `AND` tuşa basıldığını <xref:System.Windows.Forms.Control.ModifierKeys%2A> anlamak için, özelliği ile bit <xref:System.Windows.Forms.Keys> düzeyinde işlecini ve sabit listesi değerini kullanın. Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi içinde SHIFT tuşuna basılıp basılmadığını nasıl belirleyeceğini gösterir.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
- [Nasıl yapılır: Visual Basic için CapsLock 'ın açık olup olmadığını belirleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
