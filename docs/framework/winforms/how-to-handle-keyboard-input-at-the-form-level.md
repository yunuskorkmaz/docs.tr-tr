---
title: 'Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa1a7cb7dbddc541445e5bee798261a682036b0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="4b4fa-102">Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme</span><span class="sxs-lookup"><span data-stu-id="4b4fa-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="4b4fa-103">Windows Forms Denetim iletileri düşmeden önce klavye iletileri form düzeyinde işleme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="4b4fa-104">Bu konu, bu görevin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="4b4fa-105">Form düzeyinde bir klavye ileti işleme</span><span class="sxs-lookup"><span data-stu-id="4b4fa-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="4b4fa-106">İşlemek <xref:System.Windows.Forms.Control.KeyPress> veya <xref:System.Windows.Forms.Control.KeyDown> başlangıç formu ve kümesi olay <xref:System.Windows.Forms.Form.KeyPreview%2A> forma özelliğinin `true` böylece form üzerinde herhangi bir denetim düşmeden önce klavye iletileri form tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="4b4fa-107">Aşağıdaki kod örneği tanıtıcıları <xref:System.Windows.Forms.Control.KeyPress> tüm sayı tuşları algılama ve '1', '4' ve '7' tüketen olay.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="4b4fa-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b4fa-108">Example</span></span>  
 <span data-ttu-id="4b4fa-109">Aşağıdaki kod örneği, yukarıdaki örnek için tüm uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="4b4fa-110">Uygulama içeren bir <xref:System.Windows.Forms.TextBox> odağı taşımanızı sağlayan birkaç diğer denetimlerle birlikte <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="4b4fa-111"><xref:System.Windows.Forms.Control.KeyPress> Ana olay <xref:System.Windows.Forms.Form> '1', '4' ve '7' tüketir ve <xref:System.Windows.Forms.Control.KeyPress> olayı <xref:System.Windows.Forms.TextBox> kalan anahtarları görüntülenirken '2', '5' ve '8' kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="4b4fa-112">Karşılaştırma <xref:System.Windows.Forms.MessageBox> numara anahtar biraz bastığınızda çıktı <xref:System.Windows.Forms.TextBox> ile odaklanmış <xref:System.Windows.Forms.MessageBox> odak diğer denetimleri birinde olsa da bir numara tuşuna bastığınızda çıktı.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b4fa-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4b4fa-113">Compiling the Code</span></span>  
 <span data-ttu-id="4b4fa-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4b4fa-114">This example requires:</span></span>  
  
-   <span data-ttu-id="4b4fa-115">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4b4fa-116">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b4fa-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4b4fa-117">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="4b4fa-118">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4b4fa-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b4fa-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b4fa-119">See Also</span></span>  
 [<span data-ttu-id="4b4fa-120">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="4b4fa-120">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
