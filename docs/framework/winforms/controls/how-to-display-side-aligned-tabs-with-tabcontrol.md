---
title: 'Nasıl Yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532467"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="91e37-102">Nasıl Yapılır: TabControl ile Yana Hizalanmış Sekmeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="91e37-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="91e37-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Özelliği <xref:System.Windows.Forms.TabControl> yatay (üst veya alt denetim) tersine dikey (sol veya sağ kenarı boyunca denetimi), sekmeler görüntüleme destekler.</span><span class="sxs-lookup"><span data-stu-id="91e37-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="91e37-104">Varsayılan olarak, çünkü bir zayıf bir kullanıcı deneyimi bu dikey görüntü yapılandırmayı sağlar. <xref:System.Windows.Forms.TabPage.Text%2A> özelliği <xref:System.Windows.Forms.TabPage> nesne görsel stiller etkinken sekmesinde görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="91e37-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="91e37-105">Sekme içindeki metnin yönünü denetlemek için doğrudan yolu yoktur. Sahibi kullanabilirsiniz Çiz <xref:System.Windows.Forms.TabControl> bu deneyimini geliştirmek için.</span><span class="sxs-lookup"><span data-stu-id="91e37-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="91e37-106">Aşağıdaki yordam nasıl "sahibi çizin" özelliğini kullanarak soldan sağa çalıştıran sekmesini metinle sağa hizalı sekmeler işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91e37-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="91e37-107">Sağa hizalı sekmelerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="91e37-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="91e37-108">Ekleme bir <xref:System.Windows.Forms.TabControl> formunuza.</span><span class="sxs-lookup"><span data-stu-id="91e37-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="91e37-109">Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğine <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="91e37-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="91e37-110">Ayarlama <xref:System.Windows.Forms.TabControl.SizeMode%2A> özelliğine <xref:System.Windows.Forms.TabSizeMode.Fixed>, böylece tüm sekmeler aynı genişliği.</span><span class="sxs-lookup"><span data-stu-id="91e37-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="91e37-111">Ayarlama <xref:System.Windows.Forms.TabControl.ItemSize%2A> tercih edilen özelliğine sabit sekmeleri boyutu.</span><span class="sxs-lookup"><span data-stu-id="91e37-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="91e37-112">Aklınızda <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği, sekmeler en üstte, gibi davranarak sağa hizalı olsa davranır.</span><span class="sxs-lookup"><span data-stu-id="91e37-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="91e37-113">Sonuç olarak, daha geniş sekmeleri yapmak için değiştirmelisiniz <xref:System.Drawing.Size.Height%2A> özelliği ve bunları eninden yapmak için değiştirmelisiniz <xref:System.Drawing.Size.Width%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="91e37-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="91e37-114">Aşağıdaki kod örneği ile en iyi sonuç için kümesi <xref:System.Drawing.Size.Width%2A> 25 sekmelerinin ve <xref:System.Drawing.Size.Height%2A> 100.</span><span class="sxs-lookup"><span data-stu-id="91e37-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="91e37-115">Ayarlama <xref:System.Windows.Forms.TabControl.DrawMode%2A> özelliğine <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="91e37-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="91e37-116">Tanımlamak için bir işleyici <xref:System.Windows.Forms.TabControl.DrawItem> olayı <xref:System.Windows.Forms.TabControl> soldan sağa metnin işler.</span><span class="sxs-lookup"><span data-stu-id="91e37-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="91e37-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91e37-117">See Also</span></span>  
 [<span data-ttu-id="91e37-118">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="91e37-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
