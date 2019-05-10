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
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211648"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="37976-102">Nasıl yapılır: Windows Forms’da Denetimleri Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="37976-102">How to: Position Controls on Windows Forms</span></span>

<span data-ttu-id="37976-103">Yerleştirmenize, Visual Studio'da Windows Form Tasarımcısı'nı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="37976-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="37976-104">Windows Form Tasarımcısı'nın tasarım yüzeyinde bir denetimi getirin</span><span class="sxs-lookup"><span data-stu-id="37976-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="37976-105">Visual Studio'da denetimi fareyle uygun konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="37976-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="37976-106">Denetimi seçin ve bunu bir ok ile daha hassas şekilde yerleştirmek için anahtarları taşıyın.</span><span class="sxs-lookup"><span data-stu-id="37976-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="37976-107">Ayrıca, *dayama çizgileri* tam olarak, form üzerindeki denetimleri yerleştirme yardımcı.</span><span class="sxs-lookup"><span data-stu-id="37976-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="37976-108">Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="37976-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="37976-109">Özellikler penceresini kullanarak bir denetimi getirin</span><span class="sxs-lookup"><span data-stu-id="37976-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="37976-110">Visual Studio'da yerleştirmek istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="37976-110">In Visual Studio, click the control you want to position.</span></span>

2. <span data-ttu-id="37976-111">İçinde **özellikleri** penceresinde, tür değerleri için <xref:System.Windows.Forms.Control.Location%2A> denetim kapsayıcısı içinden konumuna bağlı olarak, bir virgülle ayrılmış bir özellik.</span><span class="sxs-lookup"><span data-stu-id="37976-111">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

     <span data-ttu-id="37976-112">İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülen kapsayıcı alanının mesafe sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="37976-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="37976-113">İstediğiniz ölçekte çalışma yapabilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerler.</span><span class="sxs-lookup"><span data-stu-id="37976-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="37976-114">Bir denetimin program aracılığıyla getirin</span><span class="sxs-lookup"><span data-stu-id="37976-114">Position a control programmatically</span></span>

1. <span data-ttu-id="37976-115">Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetimin özellik bir <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="37976-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="37976-116">Denetim konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik.</span><span class="sxs-lookup"><span data-stu-id="37976-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="37976-117">Bir denetimin konumu programlı olarak Artır</span><span class="sxs-lookup"><span data-stu-id="37976-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="37976-118">Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetim noktasının X koordinatı artırmak için alt özellik.</span><span class="sxs-lookup"><span data-stu-id="37976-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="37976-119">Kullanım <xref:System.Windows.Forms.Control.Location%2A> denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="37976-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="37976-120">Tek tek bir konum belirlemek için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik.</span><span class="sxs-lookup"><span data-stu-id="37976-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="37976-121">X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="37976-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="37976-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37976-122">See also</span></span>

- [<span data-ttu-id="37976-123">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="37976-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="37976-124">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="37976-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="37976-125">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="37976-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="37976-126">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="37976-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="37976-127">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="37976-127">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="37976-128">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="37976-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="37976-129">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="37976-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="37976-130">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="37976-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="37976-131">[Nasıl yapılır: Windows formlarının ekran konumunu ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37976-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
