---
title: 'Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 5f3be7467aad8b14aa67dc57b8c23e585a62fa25
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704494"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme
Bir Windows Forms için ayarlayabileceğiniz birden fazla gecikme değerleri vardır <xref:System.Windows.Forms.ToolTip> bileşeni. Tüm bu özellikler için ölçü birimini milisaniyedir. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Özelliği belirler ilişkili denetim için görüntülenecek araç ipucu dize, kullanıcının ne kadar süreyle işaret etmelidir. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Özelliği bir araç ipucu ilişkili denetimden fareyi hareket ettirdikçe görüntülenecek araç ipucu dizeler sonraki geçen milisaniye sayısını ayarlar. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Özelliği, araç ipucu dize gösterilir sürenin uzunluğunu belirler. Tek tek veya değerini ayarlayarak bu değerleri ayarlayabileceğiniz <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği; özellikleri için atanan değer baz alınarak ayarlanır gecikme <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği. Örneğin, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> N değerine ayarlanır <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> N-ayarlanır <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> değerine ayarlanır <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> beş aralıktaki (veya 5/N) ve <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> beş kez değeri olan bir değere ayarlanmış <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği (veya 5N).  
  
### <a name="to-set-the-delay"></a>Gecikme süresini ayarlamak için  
  
1.  Bu örnekte gösterildiği gibi aşağıdaki özellikleri ayarlayın.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ToolTip Bileşenine Genel Bakış](tooltip-component-overview-windows-forms.md)
- [Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip Bileşeni](tooltip-component-windows-forms.md)
