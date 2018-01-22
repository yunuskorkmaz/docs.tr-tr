---
title: "Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama"
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
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28a83a623329a7bf0162bb9feb0dc21bb73611cf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama
Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kodunda ya da Windows Form Tasarımcısı dize. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Bir araç ipucu programlı olarak ayarlamak için  
  
1.  Araç İpucu görüntüler denetimi ekleyin.  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Bir araç ipucu Designer'da ayarlamak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.  
  
2.  Araç ipucu görüntülemek veya forma ekler denetimi seçin.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın **araç ipucu ToolTip1 üzerinde** uygun bir metin dizesini değerine.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolTip Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [ToolTip Bileşeni](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
