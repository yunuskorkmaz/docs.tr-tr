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
ms.openlocfilehash: 3b15edfec25282d5a0b79ef48cabd2a27c694055
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367307"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="b5cfc-102">Nasıl yapılır: Windows Formları Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="b5cfc-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="b5cfc-103">Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilecek doğrulama olayların nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="b5cfc-104">Adlı metin kutusunda `TextBoxInput` odaklı ve her olay hakkında bilgiler adlı metin kutusuna yazılan olayları alır `TextBoxOutput` olaylar oluştuğunda sırada.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="b5cfc-105">Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5cfc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5cfc-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5cfc-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b5cfc-107">Compiling the Code</span></span>  
 <span data-ttu-id="b5cfc-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b5cfc-108">This example requires:</span></span>  
  
-   <span data-ttu-id="b5cfc-109">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b5cfc-110">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b5cfc-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b5cfc-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b5cfc-112">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b5cfc-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cfc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5cfc-113">See Also</span></span>  
 [<span data-ttu-id="b5cfc-114">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="b5cfc-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
