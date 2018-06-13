---
title: 'Nasıl yapılır: Windows Formları Denetimlerinde Kullanıcı Girdi Olaylarını İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 1faff6112f7857c2b1d6e4ac70c87f1a2adb62a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538776"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="38168-102">Nasıl yapılır: Windows Formları Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="38168-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="38168-103">Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilir doğrulama olayları nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38168-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="38168-104">Adlı metin kutusunda `TextBoxInput` odak varsa ve her olay hakkında bilgi adlı metin kutusuna yazılan olaylarını alır `TextBoxOutput` olayları yükseltilmiş sırayla.</span><span class="sxs-lookup"><span data-stu-id="38168-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="38168-105">Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.</span><span class="sxs-lookup"><span data-stu-id="38168-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38168-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="38168-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38168-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="38168-107">Compiling the Code</span></span>  
 <span data-ttu-id="38168-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="38168-108">This example requires:</span></span>  
  
-   <span data-ttu-id="38168-109">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="38168-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="38168-110">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="38168-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="38168-111">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38168-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="38168-112">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="38168-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38168-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38168-113">See Also</span></span>  
 [<span data-ttu-id="38168-114">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="38168-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
