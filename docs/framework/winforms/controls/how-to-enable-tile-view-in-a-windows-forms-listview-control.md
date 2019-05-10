---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 3244f9560467de7a63b22d279a3fd277fd14876c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609731"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="f50c1-102">Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f50c1-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="f50c1-103">Döşeme görünümü özelliği ile <xref:System.Windows.Forms.ListView> denetimi, grafik ve metinsel bilgileri arasında görsel bir denge sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f50c1-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="f50c1-104">Kutucuk görünümde bir öğe için görüntülenen metin tabanlı bilgiler tanımlanan ayrıntı görünümü için sütun bilgileri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f50c1-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="f50c1-105">Kutucuk görünümü gruplandırma veya ekleme işareti özellikleri ile birlikte çalışır <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f50c1-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="f50c1-106">Kutucuk görünümü aşağıdaki görüntüde gösterildiği gibi bir 32 x 32 piksel simgesi ve birkaç satırlık metin kullanır.</span><span class="sxs-lookup"><span data-stu-id="f50c1-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="f50c1-107">![Görünüm ListView denetiminde döşeme](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "döşeme görünümü simge ve metin")</span><span class="sxs-lookup"><span data-stu-id="f50c1-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="f50c1-108">Kutucuk görünümü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="f50c1-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="f50c1-109">Kutucukların boyutunu ayarlayarak yapabilirsiniz <xref:System.Windows.Forms.ListView.TileSize%2A> özelliği ve metin satırı ayarlayarak kutucuğunda görüntülenen <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f50c1-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50c1-110">Kutucuk görünümü yalnızca üzerinde kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f50c1-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f50c1-111">Önceki işletim sistemlerinde kutucuk görünümüne ilgili herhangi bir kod bir etkisi yoktur ve <xref:System.Windows.Forms.ListView> denetimi büyük simge görünümünde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f50c1-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="f50c1-112">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f50c1-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="f50c1-113">Kutucuk görünümü program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f50c1-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="f50c1-114">Kullanım <xref:System.Windows.Forms.View> numaralandırması <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f50c1-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="f50c1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f50c1-115">Example</span></span>  
 <span data-ttu-id="f50c1-116">Aşağıdaki kod tam örneği kutucuk görünümü kutucukları içeren üç satır metin göstermek için değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="f50c1-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="f50c1-117">Satır kaydırma önlemek için döşeme boyutunu ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="f50c1-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f50c1-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f50c1-118">Compiling the Code</span></span>  
 <span data-ttu-id="f50c1-119">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f50c1-119">This example requires:</span></span>  
  
- <span data-ttu-id="f50c1-120">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f50c1-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="f50c1-121">Bir simge dosyası yürütülebilir dosyayla aynı dizinde book.ico adı.</span><span class="sxs-lookup"><span data-stu-id="f50c1-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="f50c1-122">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f50c1-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f50c1-123">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f50c1-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50c1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f50c1-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="f50c1-125">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="f50c1-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="f50c1-126">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f50c1-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
