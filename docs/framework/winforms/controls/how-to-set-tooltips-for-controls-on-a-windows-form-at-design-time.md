---
title: 'Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211694"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama

Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kod ya da Windows Form Tasarımcısı'nda Visual Studio dize. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Bir araç ipucu programlı olarak ayarlama

1. Araç İpucu görüntüleyen denetimi ekleyin.

2. Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.

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

## <a name="set-a-tooltip-in-the-designer"></a>Bir araç ipucu Tasarımcısı'nda ayarlayın

1. Visual Studio'da ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.

2. Araç ipucunu görüntülemek veya forma ekler denetimi seçin.

3. İçinde **özellikleri** penceresinde **ToolTip1 araç ipucu** uygun bir metin dizesi değeri.

### <a name="to-remove-a-tooltip-programmatically"></a>Bir araç ipucu programlı bir şekilde kaldırmak için

1. Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.

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

## <a name="remove-a-tooltip-in-the-designer"></a>Tasarımcıda bir araç ipucu Kaldır

1. Visual Studio'da araç ipucu görüntüleyen bir denetimi seçin.

2. İçinde **özellikleri** penceresi, metni silmek **ToolTip1 araç ipucu**.

## <a name="see-also"></a>Ayrıca bkz.

- [ToolTip Bileşenine Genel Bakış](tooltip-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip Bileşeni](tooltip-component-windows-forms.md)
