---
title: 'Nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı Girdi Olaylarını İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 5dc1997dffc53632ce8b36bc5fe89e768871fd0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802445"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="df603-102">Nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="df603-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="df603-103">Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilecek doğrulama olayların nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df603-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="df603-104">Adlı metin kutusunda `TextBoxInput` odaklı ve her olay hakkında bilgiler adlı metin kutusuna yazılan olayları alır `TextBoxOutput` olaylar oluştuğunda sırada.</span><span class="sxs-lookup"><span data-stu-id="df603-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="df603-105">Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.</span><span class="sxs-lookup"><span data-stu-id="df603-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df603-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="df603-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="df603-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="df603-107">Compiling the Code</span></span>  
 <span data-ttu-id="df603-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="df603-108">This example requires:</span></span>  
  
- <span data-ttu-id="df603-109">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="df603-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="df603-110">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="df603-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="df603-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df603-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df603-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df603-112">See also</span></span>

- [<span data-ttu-id="df603-113">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="df603-113">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
