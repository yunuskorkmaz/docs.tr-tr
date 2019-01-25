---
title: 'Nasıl yapılır: Hizalama ve denetim TableLayoutPanel denetiminde uzatma'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 91464108a6ac4600c14a06b4a7dcea200d7f0254
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535937"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="cde3c-102">Nasıl yapılır: Hizalama ve denetim TableLayoutPanel denetiminde uzatma</span><span class="sxs-lookup"><span data-stu-id="cde3c-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="cde3c-103">Hizalama ve esnetme denetimlerinde bir <xref:System.Windows.Forms.TableLayoutPanel> ile <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cde3c-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cde3c-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cde3c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cde3c-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cde3c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cde3c-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cde3c-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="cde3c-107">Hizalama ve denetim Uzat</span><span class="sxs-lookup"><span data-stu-id="cde3c-107">To align and stretch a control</span></span>  
  
1.  <span data-ttu-id="cde3c-108">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="cde3c-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="cde3c-109">Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cde3c-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="cde3c-110"><xref:System.Windows.Forms.Button> Denetim hücrede ortalanır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3.  <span data-ttu-id="cde3c-111">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="cde3c-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="cde3c-112"><xref:System.Windows.Forms.Button> Denetim genişliği eşleşecek şekilde uzatır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4.  <span data-ttu-id="cde3c-113">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="cde3c-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="cde3c-114"><xref:System.Windows.Forms.Button> Denetim hücre yüksekliği eşleşecek şekilde uzatır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5.  <span data-ttu-id="cde3c-115">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="cde3c-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="cde3c-116"><xref:System.Windows.Forms.Button> Hücreyi dolduracak şekilde denetimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="cde3c-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6.  <span data-ttu-id="cde3c-117">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="cde3c-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="cde3c-118"><xref:System.Windows.Forms.Button> Denetimi tipini özgün boyutuna döner ve hücresinin sol üst köşeye taşır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="cde3c-119">**Windows Form Tasarımcısı** ayarladı <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="cde3c-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7.  <span data-ttu-id="cde3c-120">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="cde3c-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="cde3c-121"><xref:System.Windows.Forms.Button> Denetimi hücrenin sağ alt köşeye taşır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8.  <span data-ttu-id="cde3c-122">Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="cde3c-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="cde3c-123"><xref:System.Windows.Forms.Button> Denetimi hücrenin merkezine taşır.</span><span class="sxs-lookup"><span data-stu-id="cde3c-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde3c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cde3c-124">See also</span></span>
- [<span data-ttu-id="cde3c-125">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="cde3c-125">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
