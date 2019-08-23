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
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="ab7fd-102">Nasıl yapılır: Hangi Değiştirici Tuşa Basıldığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="ab7fd-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="ab7fd-103">Kullanıcının tuş vuruşlarını kabul eden bir uygulama oluşturduğunuzda, SHIFT, ALT ve CTRL tuşları gibi değiştirici tuşları izlemek de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="ab7fd-104">Değiştirici tuşa diğer anahtarlarla birlikte basıldığında veya fare tıklamasıyla, uygulamanız uygun şekilde yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="ab7fd-105">Örneğin, S harfi basılıysa bu, ekranda "S" görünmesine neden olabilir, ancak CTRL + S tuşlarına basıldığında geçerli belge kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="ab7fd-106"><xref:System.Windows.Forms.Control.KeyDown> Olayı işleyiniz <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> , olay işleyicisi tarafından <xref:System.Windows.Forms.KeyEventArgs> alınan öğesinin özelliği hangi değiştirici tuşlarına basılanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="ab7fd-107">Alternatif olarak, <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> <xref:System.Windows.Forms.KeyEventArgs> özelliği, basılan karakteri ve bit düzeyinde OR ile Birleşik değiştirici anahtarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="ab7fd-108">Ancak, <xref:System.Windows.Forms.Control.KeyPress> olayı veya bir fare olayını işliyorsa, olay işleyicisi bu bilgileri almaz.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="ab7fd-109">Bu durumda, <xref:System.Windows.Forms.Control.ModifierKeys%2A> <xref:System.Windows.Forms.Control> sınıfının özelliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ab7fd-110">Her iki durumda da, uygun <xref:System.Windows.Forms.Keys> değeri ve test ettiğiniz değeri bir bit düzeyinde ve yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="ab7fd-111"><xref:System.Windows.Forms.Keys> Sabit listesi her bir değiştirici anahtarın varyasyonlarını sunar, bu nedenle bit düzeyinde ve doğru değerle birlikte yapmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="ab7fd-112">Örneğin, <xref:System.Windows.Forms.Keys.Shift>SHIFT tuşu <xref:System.Windows.Forms.Keys.ShiftKey>,, <xref:System.Windows.Forms.Keys.LShiftKey> <xref:System.Windows.Forms.Keys.Shift>ve değiştirici anahtar olarak SHIFT 'i test etmek için doğru değer ile temsil edilir. <xref:System.Windows.Forms.Keys.RShiftKey></span><span class="sxs-lookup"><span data-stu-id="ab7fd-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="ab7fd-113">Benzer şekilde, CTRL ve alt tuşlarını değiştiriciler olarak test etmek için sırasıyla <xref:System.Windows.Forms.Keys.Control> ve <xref:System.Windows.Forms.Keys.Alt> değerlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab7fd-114">Visual Basic programcılar, <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> özelliği aracılığıyla anahtar bilgilerine de erişebilir</span><span class="sxs-lookup"><span data-stu-id="ab7fd-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="ab7fd-115">Hangi değiştirici tuşa basıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="ab7fd-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="ab7fd-116">Belirli bir değiştirici `AND` tuşa basıldığını <xref:System.Windows.Forms.Control.ModifierKeys%2A> anlamak için, özelliği ile bit <xref:System.Windows.Forms.Keys> düzeyinde işlecini ve sabit listesi değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="ab7fd-117">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi içinde SHIFT tuşuna basılıp basılmadığını nasıl belirleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ab7fd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab7fd-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="ab7fd-119">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="ab7fd-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="ab7fd-120">[Nasıl yapılır: Visual Basic için CapsLock 'ın açık olup olmadığını belirleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab7fd-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
