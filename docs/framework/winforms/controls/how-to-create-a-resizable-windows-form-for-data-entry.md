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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396022"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="fe309-102">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe309-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="fe309-103">İyi bir düzen, üst form boyutlarındaki değişikliklere iyi yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="fe309-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="fe309-104">Form boyutları değiştikçe, denetimlerinizi yeniden boyutlandırmak ve düzenli bir şekilde konumlandırmak üzere formunuzun yerleşimini düzenlemek için <xref:System.Windows.Forms.TableLayoutPanel> denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe309-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="fe309-105">@No__t-0 denetimi, denetimlerinizin içeriklerinde yapılan değişiklikler düzende değişikliklere neden olduğunda da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="fe309-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="fe309-106">Bu yordamda ele alınan işlem, Visual Studio ortamı içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe309-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="fe309-107">Ayrıca bkz. [Izlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fe309-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe309-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe309-108">Example</span></span>  
 <span data-ttu-id="fe309-109">Aşağıdaki örnek, Kullanıcı formu yeniden boyutlandırdığında iyi yanıt veren bir düzen oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetiminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe309-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="fe309-110">Ayrıca, yerelleştirmeye iyi yanıt veren bir düzen gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe309-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe309-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe309-111">Compiling the Code</span></span>  
 <span data-ttu-id="fe309-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fe309-112">This example requires:</span></span>  
  
- <span data-ttu-id="fe309-113">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fe309-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe309-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe309-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="fe309-115">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="fe309-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="fe309-116">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="fe309-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
