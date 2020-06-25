---
title: 'Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama'
description: Program aracılığıyla denetimleri için araç Ipuçları ayarlamayı öğrenin veya Visual Studio 'daki Windows Form Tasarımcısı.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325978"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Nasıl yapılır: tasarım zamanında Windows formundaki denetimler için araç Ipuçları ayarlama

<xref:System.Windows.Forms.ToolTip>Visual Studio 'da veya Windows Form Tasarımcısı kodda bir dize ayarlayabilirsiniz. Bileşen hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bkz. [ToolTip bileşenine genel bakış](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Program aracılığıyla bir araç Ipucu ayarlama

1. Araç Ipucunu görüntüleyen denetimi ekleyin.

2. <xref:System.Windows.Forms.ToolTip.SetToolTip%2A>Bileşenin yöntemini kullanın <xref:System.Windows.Forms.ToolTip> .

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>Tasarımcıda araç Ipucu ayarlama

1. Visual Studio 'da <xref:System.Windows.Forms.ToolTip> forma bir bileşen ekleyin.

2. Araç Ipucunu görüntüleyecek denetimi seçin veya forma ekleyin.

3. **Özellikler** penceresinde, **ToolTip1 değerindeki araç ipucunu** uygun bir metin dizesi olarak ayarlayın.

### <a name="to-remove-a-tooltip-programmatically"></a>Araç Ipucunu programlama yoluyla kaldırma

1. <xref:System.Windows.Forms.ToolTip.SetToolTip%2A>Bileşenin yöntemini kullanın <xref:System.Windows.Forms.ToolTip> .

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>Tasarımcıda araç Ipucunu kaldırma

1. Visual Studio 'da araç Ipucunu görüntüleyen denetimi seçin.

2. **Özellikler** penceresinde, **ToolTip1 üzerindeki araç ipucunda**bulunan metni silin.

## <a name="see-also"></a>Ayrıca bkz.

- [ToolTip Bileşenine Genel Bakış](tooltip-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip Bileşeni](tooltip-component-windows-forms.md)
