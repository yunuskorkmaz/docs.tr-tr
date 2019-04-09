---
title: 'Nasıl yapılır: Windows Forms’da Denetimleri Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 22225c97ec082022cb609e47d3cafcdcc052143d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132801"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="df646-102">Nasıl yapılır: Windows Forms’da Denetimleri Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="df646-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="df646-103">Yerleştirmenize, Windows Forms Tasarımcısı'nı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="df646-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df646-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="df646-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="df646-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="df646-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="df646-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="df646-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="df646-107">Windows Form Tasarımcısı'nın tasarım yüzeyinde bir denetimi konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="df646-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="df646-108">Denetim fare ile uygun konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="df646-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df646-109">Denetimi seçin ve bunu bir ok ile daha hassas şekilde yerleştirmek için anahtarları taşıyın.</span><span class="sxs-lookup"><span data-stu-id="df646-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="df646-110">Ayrıca, *dayama çizgileri* tam olarak, form üzerindeki denetimleri yerleştirme yardımcı.</span><span class="sxs-lookup"><span data-stu-id="df646-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="df646-111">Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="df646-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="df646-112">Özellikler penceresini kullanarak bir denetimi konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="df646-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="df646-113">Yerleştirmek istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df646-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="df646-114">İçinde **özellikleri** penceresinde, tür değerleri için <xref:System.Windows.Forms.Control.Location%2A> denetim kapsayıcısı içinden konumuna bağlı olarak, bir virgülle ayrılmış bir özellik.</span><span class="sxs-lookup"><span data-stu-id="df646-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="df646-115">İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülen kapsayıcı alanının mesafe sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="df646-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df646-116">İstediğiniz ölçekte çalışma yapabilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerler.</span><span class="sxs-lookup"><span data-stu-id="df646-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="df646-117">Bir denetimin program aracılığıyla konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="df646-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="df646-118">Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetimin özellik bir <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="df646-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="df646-119">Denetim konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik.</span><span class="sxs-lookup"><span data-stu-id="df646-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="df646-120">Bir denetimin konumu programlı olarak artırmak için</span><span class="sxs-lookup"><span data-stu-id="df646-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="df646-121">Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetim noktasının X koordinatı artırmak için alt özellik.</span><span class="sxs-lookup"><span data-stu-id="df646-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="df646-122">Kullanım <xref:System.Windows.Forms.Control.Location%2A> denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="df646-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="df646-123">Tek tek bir konum belirlemek için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik.</span><span class="sxs-lookup"><span data-stu-id="df646-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="df646-124">X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="df646-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df646-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df646-125">See also</span></span>

- [<span data-ttu-id="df646-126">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="df646-126">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="df646-127">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="df646-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="df646-128">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="df646-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="df646-129">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="df646-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="df646-130">Windows Formlarında Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="df646-130">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="df646-131">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="df646-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="df646-132">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="df646-132">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="df646-133">İşlevlere Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="df646-133">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="df646-134">Nasıl yapılır: Windows formlarının ekran konumunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="df646-134">How to: Set the Screen Location of Windows Forms</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
