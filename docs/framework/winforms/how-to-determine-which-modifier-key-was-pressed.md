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
ms.locfileid: "33540023"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="933a0-102">Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="933a0-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="933a0-103">Kullanıcının tuş vuruşlarını kabul eden bir uygulama oluşturduğunuzda, üst karakter, ALT ve CTRL tuşları gibi değiştirici tuşları izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="933a0-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="933a0-104">Değiştirici tuşa birlikte diğer anahtarlarla veya fare tıklatma ile basıldığında uygulamanızı uygun şekilde yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="933a0-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="933a0-105">Örneğin, S harfi basıldıysa bu basitçe "ekranda görünmesi bir s" neden olabilir, ancak CTRL + S anahtarları basıldıysa geçerli belge kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="933a0-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="933a0-106">İşleme, <xref:System.Windows.Forms.Control.KeyDown> olayı <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> alınan hangi değiştirici tuşları basılı tarafından olay işleyicisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="933a0-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="933a0-107">Alternatif olarak, <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> bit düzeyinde OR ile birlikte herhangi değiştirici tuşları de basıldı karakteri belirtir.</span><span class="sxs-lookup"><span data-stu-id="933a0-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="933a0-108">Ancak, işleniyorsa <xref:System.Windows.Forms.Control.KeyPress> veya fare olayın olay işleyicisi bu bilgilerini almaz.</span><span class="sxs-lookup"><span data-stu-id="933a0-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="933a0-109">Bu durumda, kullanmalısınız <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="933a0-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="933a0-110">Her iki durumda da, uygun bir bit düzeyinde AND gerçekleştirmelisiniz <xref:System.Windows.Forms.Keys> ve test ettiğiniz değerleri.</span><span class="sxs-lookup"><span data-stu-id="933a0-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="933a0-111"><xref:System.Windows.Forms.Keys> Numaralandırma Çeşitlemeler bitwise gerçekleştirmek önemlidir her değiştirici tuşa ve doğru değerle sunar.</span><span class="sxs-lookup"><span data-stu-id="933a0-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="933a0-112">Örneğin, SHIFT tuşunu tarafından temsil edilen <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> ve <xref:System.Windows.Forms.Keys.LShiftKey> SHIFT değiştirici tuşa olarak test etmek için doğru değeri <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="933a0-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="933a0-113">Benzer şekilde, DNTL ve ALT değiştiricileri test etmek için kullanması gereken <xref:System.Windows.Forms.Keys.Control> ve <xref:System.Windows.Forms.Keys.Alt> değerler, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="933a0-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="933a0-114">Visual Basic programcıları anahtar bilgileri aracılığıyla da erişebilirsiniz <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="933a0-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="933a0-115">Hangi değiştirici tuşa basıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="933a0-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="933a0-116">Bit düzeyinde kullanmak `AND` işleciyle <xref:System.Windows.Forms.Control.ModifierKeys%2A> özelliği ve değerini <xref:System.Windows.Forms.Keys> belirli değiştirici tuşa basıldığında olup olmadığını belirlemek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="933a0-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="933a0-117">Aşağıdaki kod örneğinde içinde SHIFT tuşunu basılı olup olmadığını belirlemek gösterilmiştir bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="933a0-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="933a0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="933a0-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="933a0-119">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="933a0-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="933a0-120">Nasıl yapılır: CapsLock etkin Visual Basic'te olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="933a0-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](http://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
