---
title: Denetimlerin Konumlarını Belirleme
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
ms.openlocfilehash: 144a0021c74f0fb5afec1d511315168fb28528e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735919"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms denetimleri konumlandırma

Denetimleri konumlandırmak için, Visual Studio 'da Windows Form Tasarımcısı kullanın veya <xref:System.Windows.Forms.Control.Location%2A> özelliğini belirtin.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Windows Form Tasarımcısı tasarım yüzeyine bir denetim konumlandırın

Visual Studio 'da, denetimi fareyle uygun konuma sürükleyin.

> [!NOTE]
> Denetimi seçin ve bunu daha hassas bir şekilde konumlandırmak için ok tuşlarıyla taşıyın. Ayrıca, *dayama çizgileri* denetimleri formunuza tam olarak yerleştirmekte yardımcı olur. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri yerleştirme, yama çizgileri kullanarak](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Özellikler penceresi kullanarak bir denetimi konumlandırma

1. Visual Studio 'da konumlandırmak istediğiniz denetimi seçin.

2. **Özellikler** penceresinde, denetimin kapsayıcısı içinde konumlandırmak için <xref:System.Windows.Forms.Control.Location%2A> özelliğinin değerlerini virgülle ayırarak girin.

   İlk sayı (X) kapsayıcının sol kenarlığının uzaklığı; İkinci sayı (Y), kapsayıcı alanının üst kenarlığının piksel cinsinden ölçülmüş uzaklığı.

   > [!NOTE]
   > **X** ve **Y** değerlerini tek tek yazmak için <xref:System.Windows.Forms.Control.Location%2A> özelliğini genişletebilirsiniz.

## <a name="position-a-control-programmatically"></a>Bir denetimi programlı olarak konumlandırma

1. Denetimin <xref:System.Windows.Forms.Control.Location%2A> özelliğini bir <xref:System.Drawing.Point>olarak ayarlayın.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <xref:System.Windows.Forms.Control.Left%2A> alt özelliğini kullanarak denetimin konumunun X koordinatını değiştirin.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Denetimin konumunu programlı olarak artırma

Denetimin X koordinatını artırmak için <xref:System.Windows.Forms.Control.Left%2A> alt özelliğini ayarlayın.

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
> Bir denetimin X ve Y konumlarını eşzamanlı olarak ayarlamak için <xref:System.Windows.Forms.Control.Location%2A> özelliğini kullanın. Bir konumu tek tek ayarlamak için, denetimin <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özelliğini kullanın. Bu yapı düğmenin koordinatlarının bir kopyasını içerdiğinden, düğmenin konumunu temsil eden <xref:System.Drawing.Point> yapısının X ve Y koordinatlarını örtülü olarak ayarlamaya çalışmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
- [Nasıl yapılır: Windows Forms ekran konumunu ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
