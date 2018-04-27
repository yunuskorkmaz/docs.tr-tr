---
title: 'Nasıl yapılır: Windows Formları Denetimlerinde Kullanıcı Girdi Olaylarını İşleme'
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
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7599bcbd93183aa06bb35c30e0265b9b15b966cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="137db-102">Nasıl yapılır: Windows Formları Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="137db-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="137db-103">Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilir doğrulama olayları nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="137db-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="137db-104">Adlı metin kutusunda `TextBoxInput` odak varsa ve her olay hakkında bilgi adlı metin kutusuna yazılan olaylarını alır `TextBoxOutput` olayları yükseltilmiş sırayla.</span><span class="sxs-lookup"><span data-stu-id="137db-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="137db-105">Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.</span><span class="sxs-lookup"><span data-stu-id="137db-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="137db-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="137db-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="137db-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="137db-107">Compiling the Code</span></span>  
 <span data-ttu-id="137db-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="137db-108">This example requires:</span></span>  
  
-   <span data-ttu-id="137db-109">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="137db-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="137db-110">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="137db-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="137db-111">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="137db-111">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="137db-112">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="137db-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137db-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="137db-113">See Also</span></span>  
 [<span data-ttu-id="137db-114">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="137db-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
