---
title: "Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme"
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
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 04b5394a5e5f64228635d7c23df150df9391fa44
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="79405-102">Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="79405-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="79405-103">Kısayol menüleri ve denetimleri oluşturduktan sonra kullanıcı denetimi tıklattığında verilen kısayol menüsünü görüntülemek için aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="79405-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="79405-104">Bu yordamları ilişkilendirmek bir <xref:System.Windows.Forms.ContextMenuStrip> ve bir Windows formu ile bir <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="79405-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="79405-105">Bir Windows formunda bir ContextMenuStrip ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="79405-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="79405-106">Ayarlama <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> ilişkili adı özelliğine <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="79405-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="79405-107">ToolStrip denetimi ile bir ContextMenuStrip ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="79405-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="79405-108">Denetimin ayarlamak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> ilişkili adı özelliğine <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="79405-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79405-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="79405-109">Example</span></span>  
 <span data-ttu-id="79405-110">Windows Form aşağıdaki kod örneği oluşturur ve bir <xref:System.Windows.Forms.ToolStrip>ve farklı bir ilişkilendirir <xref:System.Windows.Forms.ContextMenuStrip> denetimi ile bunların her biri.</span><span class="sxs-lookup"><span data-stu-id="79405-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="79405-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="79405-111">Compiling the Code</span></span>  
 <span data-ttu-id="79405-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="79405-112">This example requires:</span></span>  
  
-   <span data-ttu-id="79405-113">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="79405-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="79405-114">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="79405-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="79405-115">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79405-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="79405-116">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="79405-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79405-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79405-117">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="79405-118">Nasıl yapılır: Bir ContextMenuStrip'e Menü Öğeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="79405-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [<span data-ttu-id="79405-119">ContextMenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="79405-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
