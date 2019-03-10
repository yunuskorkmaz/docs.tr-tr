---
title: 'Nasıl yapılır: TableLayoutPanel denetimi içindeki satırları ve sütunları span'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: e4fc00c3966d44ba36a0c59b37ae2fa1cd431014
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703042"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="7bb29-102">Nasıl yapılır: TableLayoutPanel denetimi içindeki satırları ve sütunları span</span><span class="sxs-lookup"><span data-stu-id="7bb29-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="7bb29-103">Denetimlerini bir <xref:System.Windows.Forms.TableLayoutPanel> denetim bitişik satır ve sütunları yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb29-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bb29-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7bb29-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7bb29-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7bb29-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7bb29-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7bb29-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="7bb29-107">Satırları ve sütunları yaymasına izin</span><span class="sxs-lookup"><span data-stu-id="7bb29-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="7bb29-108">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="7bb29-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="7bb29-109">Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7bb29-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="7bb29-110">Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğini **2**.</span><span class="sxs-lookup"><span data-stu-id="7bb29-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="7bb29-111">Unutmayın <xref:System.Windows.Forms.Button> denetim birinci ve ikinci sütunların yayılır.</span><span class="sxs-lookup"><span data-stu-id="7bb29-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="7bb29-112">Ayarlama <xref:System.Windows.Forms.Button> denetimin **RowSpan** özelliğini **2**.</span><span class="sxs-lookup"><span data-stu-id="7bb29-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="7bb29-113">Unutmayın <xref:System.Windows.Forms.Button> denetimi kapsayan ilk ve ikinci satırlar.</span><span class="sxs-lookup"><span data-stu-id="7bb29-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="7bb29-114">Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğini **1**.</span><span class="sxs-lookup"><span data-stu-id="7bb29-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="7bb29-115">Unutmayın <xref:System.Windows.Forms.Button> denetimi ilk sütuna taşır ve ilk ve ikinci satırlar yayılır.</span><span class="sxs-lookup"><span data-stu-id="7bb29-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb29-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb29-116">See also</span></span>
- [<span data-ttu-id="7bb29-117">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="7bb29-117">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
