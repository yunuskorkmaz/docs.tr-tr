---
title: Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
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
ms.openlocfilehash: e47c61667a12ea9215c13bee873a668d2ad2188b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535412"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="cde5a-102">Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cde5a-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="cde5a-103">Döşeme görünümü özelliği ile <xref:System.Windows.Forms.ListView> denetim, grafik ve metin bilgi arasında görsel bir denge sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cde5a-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="cde5a-104">Döşeme görünümde bir öğe için görüntülenen metin bilgileri, ayrıntı görünümü için tanımlanan sütun bilgileri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cde5a-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="cde5a-105">Döşeme görünümü gruplandırma veya ekleme işareti özellikleri ile birlikte çalışır <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="cde5a-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="cde5a-106">Döşeme görünümü bir 32 x 32 piksel simgesi ve birkaç satırlık metin, aşağıdaki görüntüleri gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="cde5a-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="cde5a-107">![Görünüm ListView denetiminde döşeme](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="cde5a-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
<span data-ttu-id="cde5a-108">Döşeme görünümü simgeler ve metin</span><span class="sxs-lookup"><span data-stu-id="cde5a-108">Tile view icons and text</span></span>  
  
 <span data-ttu-id="cde5a-109">Döşeme görünümü etkinleştirmek için ayarlanmış <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="cde5a-109">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="cde5a-110">Ayarlayarak döşeme boyutunu ayarlayabilirsiniz <xref:System.Windows.Forms.ListView.TileSize%2A> özelliği ve ayarlayarak kutucukta görüntülenen metin satırı sayısını <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cde5a-110">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cde5a-111">Döşeme görünümü yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cde5a-111">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cde5a-112">Önceki işletim sistemlerinde döşeme görünümüne ilgili herhangi bir kod herhangi bir etkisi olmaz ve <xref:System.Windows.Forms.ListView> denetimi büyük simge görünümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cde5a-112">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="cde5a-113">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cde5a-113">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="cde5a-114">Döşeme görünümü programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cde5a-114">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="cde5a-115">Kullanım <xref:System.Windows.Forms.View> numaralandırması <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="cde5a-115">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="cde5a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="cde5a-116">Example</span></span>  
 <span data-ttu-id="cde5a-117">Aşağıdaki tam kod örneğinde üç satırlık metin göstermek için değişiklik döşeme ile döşeme görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cde5a-117">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="cde5a-118">Döşeme boyutunu satır kaydırma önlemek için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="cde5a-118">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cde5a-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cde5a-119">Compiling the Code</span></span>  
 <span data-ttu-id="cde5a-120">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cde5a-120">This example requires:</span></span>  
  
-   <span data-ttu-id="cde5a-121">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cde5a-121">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="cde5a-122">Bir simge dosyası yürütülebilir dosya ile aynı dizinde book.ico adlı.</span><span class="sxs-lookup"><span data-stu-id="cde5a-122">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="cde5a-123">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cde5a-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cde5a-124">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cde5a-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="cde5a-125">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cde5a-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde5a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cde5a-126">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="cde5a-127">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="cde5a-127">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="cde5a-128">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cde5a-128">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="cde5a-129">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="cde5a-129">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
