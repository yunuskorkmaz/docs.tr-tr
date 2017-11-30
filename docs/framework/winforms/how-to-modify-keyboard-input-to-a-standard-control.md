---
title: "Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c95ba3ef1c590f5c7e5d5e89ed05cf28c7829d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="8449d-102">Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8449d-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="8449d-103">Windows Forms kullanabilir ve klavye girişini değiştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8449d-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="8449d-104">Bir anahtarı kullanan diğer yöntemleri ve daha fazla ileti sırası aşağı olayları anahtar değeri almazsınız böylece anahtarı yöntemi veya olay işleyicisi içinde işlemeye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="8449d-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="8449d-105">Bir anahtar değiştirme yöntemleri ve olay işleyicileri daha fazla ileti sırası aşağı farklı bir anahtar değer alması için bunları bir anahtarın değerini değiştirmek için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8449d-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="8449d-106">Bu konu, bu görevlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8449d-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="8449d-107">Bir anahtarı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8449d-107">To consume a key</span></span>  
  
-   <span data-ttu-id="8449d-108">İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının `true`.</span><span class="sxs-lookup"><span data-stu-id="8449d-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="8449d-109">veya</span><span class="sxs-lookup"><span data-stu-id="8449d-109">-or-</span></span>  
  
     <span data-ttu-id="8449d-110">İçinde bir <xref:System.Windows.Forms.Control.KeyDown> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> sınıfının `true`.</span><span class="sxs-lookup"><span data-stu-id="8449d-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8449d-111">Ayarı <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliğinde <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisi engellemez <xref:System.Windows.Forms.Control.KeyPress> ve <xref:System.Windows.Forms.Control.KeyUp> için geçerli tuş vuruşu gerçekleştirilen gelen olayları.</span><span class="sxs-lookup"><span data-stu-id="8449d-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="8449d-112">Kullanım <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> özelliği bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="8449d-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="8449d-113">Aşağıdaki örnek yapılan bir alıntı olan bir `switch` inceler deyimi <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> tarafından alınan bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="8449d-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="8449d-114">Bu kod 'A' ve 'bir' karakteri anahtarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8449d-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="8449d-115">Bir standart karakter anahtarı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="8449d-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="8449d-116">İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> değeri bir sınıfa yeni karakter anahtar.</span><span class="sxs-lookup"><span data-stu-id="8449d-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="8449d-117">Aşağıdaki örnek yapılan bir alıntı olan bir `switch` 'Bir' ' B' değiştirir deyimi ve 'b' 'bir'.</span><span class="sxs-lookup"><span data-stu-id="8449d-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="8449d-118">Unutmayın <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> parametrenin ayarlanmış `false`, böylece yeni anahtar değeri diğer yöntemleri ve ileti sırasındaki olay yayılır.</span><span class="sxs-lookup"><span data-stu-id="8449d-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="8449d-119">Noncharacter anahtarı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="8449d-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="8449d-120">Geçersiz bir <xref:System.Windows.Forms.Control> Windows iletilerini işleme yöntemi WM_KEYDOWN veya WM_SYSKEYDOWN iletisi algılamak ve ayarlama <xref:System.Windows.Forms.Message.WParam%2A> özelliği <xref:System.Windows.Forms.Message> parametresi <xref:System.Windows.Forms.Keys> yeni noncharacter anahtarını temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="8449d-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="8449d-121">Aşağıdaki kod örneğinde nasıl geçersiz kılınacağı gösterilmektedir <xref:System.Windows.Forms.Control.PreProcessMessage%2A> F9 anahtarlarıyla F1 algılamak ve tüm F3 tuşuna F1 değiştirmek için bir denetim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8449d-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="8449d-122">Daha fazla bilgi için <xref:System.Windows.Forms.Control> klavye iletileri izlemesine kılabilirsiniz yöntemlerini görmek [bir Windows Forms uygulamasında kullanıcı girişi](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) ve [nasıl klavye girişi çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="8449d-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](../../../docs/framework/winforms/how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="8449d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="8449d-123">Example</span></span>  
 <span data-ttu-id="8449d-124">Aşağıdaki kod örneğinde, önceki bölümlerde kod örnekleri için tam uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8449d-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="8449d-125">Türetilen özel bir denetim uygulamanın kullandığı <xref:System.Windows.Forms.TextBox> kullanabilir ve klavye girdisini değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="8449d-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8449d-126">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8449d-126">Compiling the Code</span></span>  
 <span data-ttu-id="8449d-127">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8449d-127">This example requires:</span></span>  
  
-   <span data-ttu-id="8449d-128">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="8449d-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8449d-129">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8449d-129">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8449d-130">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="8449d-130">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="8449d-131">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8449d-131">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8449d-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8449d-132">See Also</span></span>  
 [<span data-ttu-id="8449d-133">Forms bir Windows uygulamasında klavye girdisi</span><span class="sxs-lookup"><span data-stu-id="8449d-133">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="8449d-134">Forms bir Windows uygulamasında kullanıcı girdisi</span><span class="sxs-lookup"><span data-stu-id="8449d-134">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="8449d-135">Klavye girdisi nasıl çalışır</span><span class="sxs-lookup"><span data-stu-id="8449d-135">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)
