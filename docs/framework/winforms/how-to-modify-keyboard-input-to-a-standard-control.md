---
title: 'Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964284"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="48bbf-102">Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="48bbf-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="48bbf-103">Windows Forms klavye girişini kullanma ve değiştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="48bbf-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="48bbf-104">Bir anahtarı kullanmak, bir yöntem veya olay işleyicisi içinde bir anahtarın işlenmesine, böylece ileti sırasının daha sonra gelen diğer yöntemlerin ve olayların anahtar değerini almamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="48bbf-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="48bbf-105">Bir anahtarı değiştirmek, bir anahtarın değerini değiştirmek ve bu sayede ileti sırasının daha sonra gelen Yöntem ve olay işleyicilerinin farklı bir anahtar değeri alması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48bbf-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="48bbf-106">Bu konu, bu görevlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="48bbf-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="48bbf-107">Bir anahtarı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="48bbf-107">To consume a key</span></span>  
  
- <span data-ttu-id="48bbf-108">Bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisinde, <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48bbf-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="48bbf-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="48bbf-109">-or-</span></span>  
  
     <span data-ttu-id="48bbf-110">Bir <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisinde, <xref:System.Windows.Forms.KeyEventArgs> sınıfının <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48bbf-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="48bbf-111">Olay işleyicisindeki <xref:System.Windows.Forms.Control.KeyPress> özelliği ayarlamak, ve <xref:System.Windows.Forms.Control.KeyUp> olaylarının geçerli tuş vuruşu için oluşmasını engellemez. <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.Control.KeyDown></span><span class="sxs-lookup"><span data-stu-id="48bbf-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="48bbf-112">Bu amaçla <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="48bbf-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="48bbf-113">Aşağıdaki örnek `switch` , bir <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> olay<xref:System.Windows.Forms.Control.KeyPress> işleyicisi tarafından alınan özelliğinin özelliğini incelediği bir deyimin alıntısıdır.</span><span class="sxs-lookup"><span data-stu-id="48bbf-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="48bbf-114">Bu kod ' A ' ve ' a ' karakter anahtarlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="48bbf-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="48bbf-115">Standart bir karakter anahtarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="48bbf-115">To modify a standard character key</span></span>  
  
- <span data-ttu-id="48bbf-116">Bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisinde, <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliğini yeni karakter anahtarının değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48bbf-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="48bbf-117">Aşağıdaki örnek ' a ' ile ' b `switch` ' ve ' b ' ile değiştiren bir deyimden alıntıdır.</span><span class="sxs-lookup"><span data-stu-id="48bbf-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="48bbf-118">Parametresinin özelliğinin, yeni anahtar değerinin ileti sırasındaki diğer yöntemlere `false`ve olaylara yayılması için olarak ayarlandığını unutmayın. <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs></span><span class="sxs-lookup"><span data-stu-id="48bbf-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="48bbf-119">Karakter olmayan bir anahtarı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="48bbf-119">To modify a noncharacter key</span></span>  
  
- <span data-ttu-id="48bbf-120">Windows iletilerini <xref:System.Windows.Forms.Control> işleyen, wm_keydown veya wm_syskeydown iletisini algılayan bir yöntemi geçersiz kılın ve <xref:System.Windows.Forms.Message> parametrenin <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Keys> özelliğini yeni olmayan karakter anahtarını temsil eden değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48bbf-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="48bbf-121">Aşağıdaki kod örneği, bir denetimin <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yönteminin F1 ile F9 arası bir şekilde algılanması ve tüm F3 tuşuna basarak F1 'e basmanız için nasıl geçersiz kılınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="48bbf-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="48bbf-122">Klavye iletilerini kesmeye yönelik <xref:System.Windows.Forms.Control> geçersiz kılabileceğiniz yöntemler hakkında daha fazla bilgi için, bkz. [Windows Forms uygulamasında kullanıcı girişi](user-input-in-a-windows-forms-application.md) ve [klavye girişinin nasıl çalıştığı](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="48bbf-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="48bbf-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="48bbf-123">Example</span></span>  
 <span data-ttu-id="48bbf-124">Aşağıdaki kod örneği, önceki bölümlerdeki kod örnekleri için tüm uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="48bbf-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="48bbf-125">Uygulama, klavye girişini kullanmak ve değiştirmek için <xref:System.Windows.Forms.TextBox> sınıfından türetilmiş özel bir denetim kullanır.</span><span class="sxs-lookup"><span data-stu-id="48bbf-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48bbf-126">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="48bbf-126">Compiling the Code</span></span>  
 <span data-ttu-id="48bbf-127">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="48bbf-127">This example requires:</span></span>  
  
- <span data-ttu-id="48bbf-128">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="48bbf-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48bbf-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48bbf-129">See also</span></span>

- [<span data-ttu-id="48bbf-130">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="48bbf-130">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="48bbf-131">Bir Windows Forms Uygulamasında Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="48bbf-131">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="48bbf-132">Klavye Girdisi Nasıl Çalışır</span><span class="sxs-lookup"><span data-stu-id="48bbf-132">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
