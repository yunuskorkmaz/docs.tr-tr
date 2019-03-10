---
title: 'Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 541e50a8ee9c5338acc7c5e347549fd03a0f6323
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710725"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama
Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kodda veya Windows Forms Tasarımcısı'nda bir dize. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Bir araç ipucu program üzerinden ayarlamak için  
  
1.  Araç İpucu görüntüleyen denetimi ekleyin.  
  
2.  Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Tasarımcıda bir araç ipucu ayarlamak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.  
  
2.  Araç ipucunu görüntülemek veya forma ekler denetimi seçin.  
  
3.  İçinde **özellikleri** penceresinde **ToolTip1 araç ipucu** uygun bir metin dizesi değeri.  

### <a name="to-remove-a-tooltip-programmatically"></a>Bir araç ipucu programlı bir şekilde kaldırmak için  
  
1.  Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.  
  
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
  
### <a name="to-remove-a-tooltip-in-the-designer"></a>Tasarımcıda bir araç ipucu kaldırmak için  
  
1.  Araç İpucu görüntüleyen bir denetimi seçin.  
  
2.  İçinde **özellikleri** penceresi, metni silmek **ToolTip1 araç ipucu**.  

## <a name="see-also"></a>Ayrıca bkz.
- [ToolTip Bileşenine Genel Bakış](tooltip-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip Bileşeni](tooltip-component-windows-forms.md)
