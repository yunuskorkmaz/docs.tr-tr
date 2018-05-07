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
ms.openlocfilehash: 1c89149fc07f89028b21fa513fd84dee4e890968
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme
Kullanıcının tuş vuruşlarını kabul eden bir uygulama oluşturduğunuzda, üst karakter, ALT ve CTRL tuşları gibi değiştirici tuşları izlemek isteyebilirsiniz. Değiştirici tuşa birlikte diğer anahtarlarla veya fare tıklatma ile basıldığında uygulamanızı uygun şekilde yanıt verebilir. Örneğin, S harfi basıldıysa bu basitçe "ekranda görünmesi bir s" neden olabilir, ancak CTRL + S anahtarları basıldıysa geçerli belge kaydedilebilir. İşleme, <xref:System.Windows.Forms.Control.KeyDown> olayı <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> alınan hangi değiştirici tuşları basılı tarafından olay işleyicisi belirtir. Alternatif olarak, <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> bit düzeyinde OR ile birlikte herhangi değiştirici tuşları de basıldı karakteri belirtir. Ancak, işleniyorsa <xref:System.Windows.Forms.Control.KeyPress> veya fare olayın olay işleyicisi bu bilgilerini almaz. Bu durumda, kullanmalısınız <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı. Her iki durumda da, uygun bir bit düzeyinde AND gerçekleştirmelisiniz <xref:System.Windows.Forms.Keys> ve test ettiğiniz değerleri. <xref:System.Windows.Forms.Keys> Numaralandırma Çeşitlemeler bitwise gerçekleştirmek önemlidir her değiştirici tuşa ve doğru değerle sunar. Örneğin, SHIFT tuşunu tarafından temsil edilen <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> ve <xref:System.Windows.Forms.Keys.LShiftKey> SHIFT değiştirici tuşa olarak test etmek için doğru değeri <xref:System.Windows.Forms.Keys.Shift>. Benzer şekilde, DNTL ve ALT değiştiricileri test etmek için kullanması gereken <xref:System.Windows.Forms.Keys.Control> ve <xref:System.Windows.Forms.Keys.Alt> değerler, sırasıyla.  
  
> [!NOTE]
>  Visual Basic programcıları anahtar bilgileri aracılığıyla da erişebilirsiniz <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> özelliği  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Hangi değiştirici tuşa basıldığını belirleme  
  
-   Bit düzeyinde kullanmak `AND` işleciyle <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği ve değerini <xref:System.Windows.Forms.Keys> belirli değiştirici tuşa basıldığında olup olmadığını belirlemek için numaralandırması. Aşağıdaki kod örneğinde içinde SHIFT tuşunu basılı olup olmadığını belirlemek gösterilmiştir bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Bir Windows Forms Uygulamasında Klavye Girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Nasıl yapılır: CapsLock etkin Visual Basic'te olup olmadığını belirleme](http://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
