---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040357"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="b833f-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b833f-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="b833f-103"><xref:System.Windows.Forms.ListView> Denetimin kutucuk görünümü özelliği, grafik ve metin bilgileri arasında görsel bir denge sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b833f-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="b833f-104">Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b833f-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="b833f-105">Döşeme görünümü, <xref:System.Windows.Forms.ListView> denetimdeki gruplandırma ya da ekleme işareti özellikleriyle birlikte işlev görür.</span><span class="sxs-lookup"><span data-stu-id="b833f-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="b833f-106">Kutucuk görünümü, aşağıdaki görüntüde gösterildiği gibi bir 32 x 32 simgesi ve birkaç satırlık metin kullanır.</span><span class="sxs-lookup"><span data-stu-id="b833f-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="b833f-107">![ListView denetimindeki kutucuk görünümü](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")</span><span class="sxs-lookup"><span data-stu-id="b833f-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="b833f-108">Kutucuk görünümü özellikleri ve yöntemleri her öğe için hangi sütun alanlarının gösterileceğini belirtmenize ve bir kutucuk görünümü penceresindeki tüm öğelerin boyutunu ve görünümünü topluca denetleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b833f-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="b833f-109">Açıklık açısından, bir kutucukta metnin ilk satırı her zaman öğenin adıdır; değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b833f-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="b833f-110">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b833f-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b833f-111">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b833f-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b833f-112">Kutucuk görünümü yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b833f-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b833f-113">Önceki işletim sistemlerinde, kutucuk görünümüyle ilgili tüm kodlar etkisizdir ve <xref:System.Windows.Forms.ListView> denetim büyük simge görünümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b833f-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="b833f-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b833f-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="b833f-115">Tasarımcıda kutucuk görünümünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b833f-115">To set tile view in the designer</span></span>

1. <span data-ttu-id="b833f-116">Visual Studio 'da, formunuzdaki <xref:System.Windows.Forms.ListView> denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="b833f-116">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="b833f-117">**Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.View%2A> özelliği seçin ve **kutucuk**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b833f-117">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b833f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b833f-118">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="b833f-119">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b833f-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
