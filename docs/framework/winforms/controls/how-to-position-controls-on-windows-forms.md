---
title: Denetimlerin Konumlarını Belirleme
description: Denetimlerinizi konumlandırmak için Visual Studio 'daki Windows Form Tasarımcısı veya Location özelliğini kullanmayı öğrenin.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0aa3faade71e0f7e0a9d5e676327a80747524b8c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904305"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="aa326-103">Nasıl yapılır: Windows Forms denetimleri konumlandırma</span><span class="sxs-lookup"><span data-stu-id="aa326-103">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="aa326-104">Denetimleri konumlandırmak için, Visual Studio 'da Windows Form Tasarımcısı kullanın veya <xref:System.Windows.Forms.Control.Location%2A> özelliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="aa326-104">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="aa326-105">Windows Form Tasarımcısı tasarım yüzeyine bir denetim konumlandırın</span><span class="sxs-lookup"><span data-stu-id="aa326-105">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="aa326-106">Visual Studio 'da, denetimi fareyle uygun konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="aa326-106">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="aa326-107">Denetimi seçin ve bunu daha hassas bir şekilde konumlandırmak için ok tuşlarıyla taşıyın.</span><span class="sxs-lookup"><span data-stu-id="aa326-107">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="aa326-108">Ayrıca, *dayama çizgileri* denetimleri formunuza tam olarak yerleştirmekte yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="aa326-108">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="aa326-109">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri yerleştirme, yama çizgileri kullanarak](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="aa326-109">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="aa326-110">Özellikler penceresi kullanarak bir denetimi konumlandırma</span><span class="sxs-lookup"><span data-stu-id="aa326-110">Position a control using the Properties window</span></span>

1. <span data-ttu-id="aa326-111">Visual Studio 'da konumlandırmak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="aa326-111">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="aa326-112">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Location%2A> denetimin kapsayıcısı içindeki konumunu konumlandırmak için, özelliğin değerlerini virgülle ayırarak girin.</span><span class="sxs-lookup"><span data-stu-id="aa326-112">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="aa326-113">İlk sayı (X) kapsayıcının sol kenarlığının uzaklığı; İkinci sayı (Y), kapsayıcı alanının üst kenarlığının piksel cinsinden ölçülmüş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="aa326-113">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="aa326-114"><xref:System.Windows.Forms.Control.Location%2A>Özelliği tek tek **X** ve **Y** değerlerini yazmak için genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa326-114">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="aa326-115">Bir denetimi programlı olarak konumlandırma</span><span class="sxs-lookup"><span data-stu-id="aa326-115">Position a control programmatically</span></span>

1. <span data-ttu-id="aa326-116"><xref:System.Windows.Forms.Control.Location%2A>Denetimin özelliğini bir olarak ayarlayın <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="aa326-116">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="aa326-117">Alt özelliğini kullanarak denetimin konumunun X koordinatını değiştirin <xref:System.Windows.Forms.Control.Left%2A> .</span><span class="sxs-lookup"><span data-stu-id="aa326-117">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="aa326-118">Denetimin konumunu programlı olarak artırma</span><span class="sxs-lookup"><span data-stu-id="aa326-118">Increment a control's location programmatically</span></span>

<span data-ttu-id="aa326-119"><xref:System.Windows.Forms.Control.Left%2A>Denetimin X koordinatını artırmak için alt özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="aa326-119">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="aa326-120"><xref:System.Windows.Forms.Control.Location%2A>Bir denetimin X ve Y konumlarını eşzamanlı olarak ayarlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa326-120">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="aa326-121">Bir konumu tek tek ayarlamak için denetimin <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa326-121">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="aa326-122"><xref:System.Drawing.Point>Bu yapı düğmenin koordinatlarının bir kopyasını içerdiğinden, düğmenin konumunu temsil eden yapının X ve Y koordinatlarını örtülü olarak ayarlamaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="aa326-122">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa326-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa326-123">See also</span></span>

- [<span data-ttu-id="aa326-124">Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="aa326-124">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="aa326-125">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'ta Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aa326-125">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="aa326-126">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'ta Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aa326-126">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="aa326-127">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aa326-127">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="aa326-128">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="aa326-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="aa326-129">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="aa326-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="aa326-130">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="aa326-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="aa326-131">[Nasıl yapılır: Windows Forms ekran konumunu ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa326-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
