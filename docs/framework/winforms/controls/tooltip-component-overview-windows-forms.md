---
title: ToolTip Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741908"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> bileşeni, Kullanıcı denetimlere işaret ediyorsa metni görüntüler. Araç Ipucu, herhangi bir denetimle ilişkilendirilebilir. Bu bileşenin örnek kullanımı: bir formda yer kazanmak için, bir düğme üzerinde küçük bir simge görüntüleyebilir ve düğmenin işlevini açıklamak için araç Ipucu kullanabilirsiniz.  
  
## <a name="working-with-the-tooltip-component"></a>Araç Ipucu bileşeniyle çalışma  
 <xref:System.Windows.Forms.ToolTip> bileşeni, bir Windows formunda veya başka bir kapsayıcıda birden çok denetime `ToolTip` özelliği sağlar. Örneğin, bir forma bir <xref:System.Windows.Forms.ToolTip> bileşeni yerleştirirseniz, bir <xref:System.Windows.Forms.TextBox> denetimi için "adınızı buraya yazın" ve bir <xref:System.Windows.Forms.Button> denetimi için "değişiklikleri kaydetmek için buraya tıklayın" seçeneğini görüntüleyebilirsiniz.  
  
 <xref:System.Windows.Forms.ToolTip> bileşenin temel yöntemleri <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> ve <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Denetimler için görüntülenecek araç Ipuçlarını ayarlamak için <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: tasarım zamanında Windows formundaki denetimler Için araç Ipuçlarını ayarlama](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Anahtar özellikler, araç Ipucunun görünmesi için `true` olarak ayarlanması gereken <xref:System.Windows.Forms.ToolTip.Active%2A>ve araç ipucu dizesinin gösterildiği zaman uzunluğunu, kullanıcının araç Ipucu için denetimi ne kadar süreceği ve sonraki araç Ipucu pencerelerinin görünmesi için ne kadar sürdüğünü belirleyen <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolTip>
- [Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
