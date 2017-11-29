---
title: "Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ff1096e6397f4422e0fbf6400a87041cfac6470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="f08da-102">Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="f08da-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="f08da-103">Denetimleri getirin, Windows Form Tasarımcısı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f08da-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f08da-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f08da-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f08da-105">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f08da-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f08da-106">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f08da-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="f08da-107">Windows Form Tasarımcısı tasarım yüzeyine denetim konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="f08da-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="f08da-108">Denetim fareyle uygun konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f08da-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f08da-109">Denetimi seçin ve onu oklu daha kesin olarak konumlandırmak için anahtarları taşıyın.</span><span class="sxs-lookup"><span data-stu-id="f08da-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="f08da-110">Ayrıca, *dayama çizgileri* tam olarak formunuza denetimler yerleştirme yardımcı.</span><span class="sxs-lookup"><span data-stu-id="f08da-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="f08da-111">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak dayama çizgileri düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="f08da-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="f08da-112">Özellikler penceresini kullanarak denetim konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="f08da-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="f08da-113">Yerleştirmek istediğiniz denetimi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f08da-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="f08da-114">İçinde **özellikleri** penceresinde, türü değerleri için <xref:System.Windows.Forms.Control.Location%2A> kontrolün kapsayıcı içindeki denetim konumuna bağlı olarak, bir virgülle ayrılmış özelliği.</span><span class="sxs-lookup"><span data-stu-id="f08da-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="f08da-115">İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülür kapsayıcı alanının mesafe sayıdır.</span><span class="sxs-lookup"><span data-stu-id="f08da-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f08da-116">Genişletebilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerleri.</span><span class="sxs-lookup"><span data-stu-id="f08da-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="f08da-117">Bir denetim programlı olarak konumlandırmak için</span><span class="sxs-lookup"><span data-stu-id="f08da-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="f08da-118">Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetiminin özelliği bir <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="f08da-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="f08da-119">Denetimin konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik öneki.</span><span class="sxs-lookup"><span data-stu-id="f08da-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="f08da-120">Bir denetimin konumunu programlı olarak artırmak için</span><span class="sxs-lookup"><span data-stu-id="f08da-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="f08da-121">Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetimi X koordinatını artırmak için alt özellik öneki.</span><span class="sxs-lookup"><span data-stu-id="f08da-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
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
    >  <span data-ttu-id="f08da-122">Kullanım <xref:System.Windows.Forms.Control.Location%2A> bir denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="f08da-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="f08da-123">Tek tek bir konum ayarlamak için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik öneki.</span><span class="sxs-lookup"><span data-stu-id="f08da-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="f08da-124">X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="f08da-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08da-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f08da-125">See Also</span></span>  
 [<span data-ttu-id="f08da-126">Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="f08da-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="f08da-127">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="f08da-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="f08da-128">İzlenecek yol: Bir TableLayoutPanel kullanarak Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="f08da-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="f08da-129">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="f08da-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="f08da-130">Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="f08da-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="f08da-131">Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma</span><span class="sxs-lookup"><span data-stu-id="f08da-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="f08da-132">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="f08da-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="f08da-133">Windows Forms denetimleri işlevi</span><span class="sxs-lookup"><span data-stu-id="f08da-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="f08da-134">Nasıl yapılır: Windows Forms ekran konumunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="f08da-134">How to: Set the Screen Location of Windows Forms</span></span>](http://msdn.microsoft.com/en-us/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
