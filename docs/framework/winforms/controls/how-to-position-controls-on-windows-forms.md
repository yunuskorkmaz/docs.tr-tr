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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987074"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="6a05b-102">Nasıl yapılır: Windows Forms denetimleri konumlandırma</span><span class="sxs-lookup"><span data-stu-id="6a05b-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="6a05b-103">Denetimleri konumlandırmak için, Visual Studio 'da Windows Form Tasarımcısı kullanın veya <xref:System.Windows.Forms.Control.Location%2A> özelliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6a05b-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="6a05b-104">Windows Form Tasarımcısı tasarım yüzeyine bir denetim konumlandırın</span><span class="sxs-lookup"><span data-stu-id="6a05b-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="6a05b-105">Visual Studio 'da, denetimi fareyle uygun konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="6a05b-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="6a05b-106">Denetimi seçin ve bunu daha hassas bir şekilde konumlandırmak için ok tuşlarıyla taşıyın.</span><span class="sxs-lookup"><span data-stu-id="6a05b-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="6a05b-107">Ayrıca, *dayama çizgileri* denetimleri formunuza tam olarak yerleştirmekte yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6a05b-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="6a05b-108">Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms denetimleri, snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)kullanarak düzenleme.</span><span class="sxs-lookup"><span data-stu-id="6a05b-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="6a05b-109">Özellikler penceresi kullanarak bir denetimi konumlandırma</span><span class="sxs-lookup"><span data-stu-id="6a05b-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="6a05b-110">Visual Studio 'da konumlandırmak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="6a05b-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="6a05b-111">**Özellikler** penceresinde, denetimin kapsayıcısı içindeki konumunu konumlandırmak için <xref:System.Windows.Forms.Control.Location%2A> , özelliğin değerlerini virgülle ayırarak girin.</span><span class="sxs-lookup"><span data-stu-id="6a05b-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="6a05b-112">İlk sayı (X) kapsayıcının sol kenarlığının uzaklığı; İkinci sayı (Y), kapsayıcı alanının üst kenarlığının piksel cinsinden ölçülmüş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6a05b-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6a05b-113"><xref:System.Windows.Forms.Control.Location%2A> Özelliği tek tek **X** ve **Y** değerlerini yazmak için genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a05b-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="6a05b-114">Bir denetimi programlı olarak konumlandırma</span><span class="sxs-lookup"><span data-stu-id="6a05b-114">Position a control programmatically</span></span>

1. <span data-ttu-id="6a05b-115">Denetimin özelliğini bir <xref:System.Drawing.Point>olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="6a05b-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="6a05b-116"><xref:System.Windows.Forms.Control.Left%2A> Alt özelliğini kullanarak denetimin konumunun X koordinatını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6a05b-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="6a05b-117">Denetimin konumunu programlı olarak artırma</span><span class="sxs-lookup"><span data-stu-id="6a05b-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="6a05b-118">Denetimin X koordinatını artırmak için altözelliğiayarlayın.<xref:System.Windows.Forms.Control.Left%2A></span><span class="sxs-lookup"><span data-stu-id="6a05b-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="6a05b-119">Bir denetimin X ve Y konumlarını eşzamanlı olarak ayarlamak için özelliğinikullanın.<xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="6a05b-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="6a05b-120">Bir konumu tek tek ayarlamak için <xref:System.Windows.Forms.Control.Left%2A> denetimin (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a05b-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="6a05b-121">Bu yapı düğmenin koordinatlarının bir kopyasını içerdiğinden, düğmenin konumunu temsil eden <xref:System.Drawing.Point> yapının X ve Y koordinatlarını örtülü olarak ayarlamaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="6a05b-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a05b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a05b-122">See also</span></span>

- [<span data-ttu-id="6a05b-123">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="6a05b-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="6a05b-124">İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6a05b-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="6a05b-125">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6a05b-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="6a05b-126">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6a05b-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="6a05b-127">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="6a05b-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="6a05b-128">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="6a05b-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="6a05b-129">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="6a05b-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="6a05b-130">[Nasıl yapılır: Windows Forms ekran konumunu ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a05b-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
