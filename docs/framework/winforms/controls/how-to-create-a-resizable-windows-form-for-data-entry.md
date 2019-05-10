---
title: 'Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 724dfa79358548530eab49683f1cb2db55f889c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625985"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="77582-102">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="77582-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="77582-103">İyi bir düzen değişiklikleri kendi üst formunun boyutları için de yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="77582-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="77582-104">Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> yeniden boyutlandırabilir ve denetimleri tutarlı bir şekilde form denetiminin boyutlarını değiştikçe konumlandırmak için formun yerleşimini düzenlemeyi denetimi.</span><span class="sxs-lookup"><span data-stu-id="77582-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="77582-105"><xref:System.Windows.Forms.TableLayoutPanel> Denetimidir de yararlıdır düzen değişiklikleri neden denetimlerinizi içeriğini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="77582-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="77582-106">Visual Studio ortamında bu yordamda bahsedilen işlem yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="77582-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="77582-107">Ayrıca bkz: [izlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="77582-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77582-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="77582-108">Example</span></span>  
 <span data-ttu-id="77582-109">Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.TableLayoutPanel> zaman kullanıcı formu boyutlandırır iyi cevap veren bir düzen oluşturmak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="77582-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="77582-110">Ayrıca, yerelleştirmeye iyi cevap veren bir düzen gösterir.</span><span class="sxs-lookup"><span data-stu-id="77582-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77582-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="77582-111">Compiling the Code</span></span>  
 <span data-ttu-id="77582-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="77582-112">This example requires:</span></span>  
  
- <span data-ttu-id="77582-113">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="77582-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="77582-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="77582-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="77582-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77582-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77582-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77582-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="77582-117">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="77582-117">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="77582-118">Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama</span><span class="sxs-lookup"><span data-stu-id="77582-118">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="77582-119">Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricileri ve tasarımcıları için resmi yönergeleri. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="77582-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
