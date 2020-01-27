---
title: Araç Ipucu bileşeni gecikmesini değiştirme
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746582"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme
Bir Windows Forms <xref:System.Windows.Forms.ToolTip> bileşeni için ayarlayabileceğiniz birden fazla gecikme değeri vardır. Tüm bu özellikler için ölçü birimi milisaniyedir. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> özelliği, kullanıcının araç Ipucu dizesinin görünmesi için ilgili denetimi ne kadar süreyle göstermesi gerektiğini belirler. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> özelliği, fare Ipucu ile ilişkili bir denetimden diğerine geçirken sonraki araç Ipucu dizelerinin görünmesi için geçen milisaniye sayısını ayarlar. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> özelliği, ToolTip dizesinin gösterdiği sürenin uzunluğunu belirler. Bu değerleri ayrı ayrı veya <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğinin değerini ayarlayarak ayarlayabilirsiniz; diğer gecikme özellikleri, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğine atanan değere göre ayarlanır. Örneğin, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> bir değeri N olarak ayarlandığında <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> N olarak ayarlanır <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>, beş (veya N/5) bölünen <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> değerine ayarlanır ve <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliğinin değeri beş kat olan bir değere ayarlanır (veya 5N).  
  
### <a name="to-set-the-delay"></a>Gecikmeyi ayarlamak için  
  
1. Aşağıdaki özellikleri bu örnekte gösterildiği gibi ayarlayın.  
  
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
- [Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip Bileşeni](tooltip-component-windows-forms.md)
