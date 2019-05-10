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
# <a name="how-to-position-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms’da Denetimleri Konumlandırma

Yerleştirmenize, Visual Studio'da Windows Form Tasarımcısı'nı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Windows Form Tasarımcısı'nın tasarım yüzeyinde bir denetimi getirin

Visual Studio'da denetimi fareyle uygun konuma sürükleyin.

> [!NOTE]
> Denetimi seçin ve bunu bir ok ile daha hassas şekilde yerleştirmek için anahtarları taşıyın. Ayrıca, *dayama çizgileri* tam olarak, form üzerindeki denetimleri yerleştirme yardımcı. Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Özellikler penceresini kullanarak bir denetimi getirin

1. Visual Studio'da yerleştirmek istediğiniz denetim tıklayın.

2. İçinde **özellikleri** penceresinde, tür değerleri için <xref:System.Windows.Forms.Control.Location%2A> denetim kapsayıcısı içinden konumuna bağlı olarak, bir virgülle ayrılmış bir özellik.

     İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülen kapsayıcı alanının mesafe sayısıdır.

    > [!NOTE]
    > İstediğiniz ölçekte çalışma yapabilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerler.

## <a name="position-a-control-programmatically"></a>Bir denetimin program aracılığıyla getirin

1. Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetimin özellik bir <xref:System.Drawing.Point>.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Denetim konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Bir denetimin konumu programlı olarak Artır

Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetim noktasının X koordinatı artırmak için alt özellik.

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
> Kullanım <xref:System.Windows.Forms.Control.Location%2A> denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir. Tek tek bir konum belirlemek için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik. X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
- [Nasıl yapılır: Windows formlarının ekran konumunu ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
