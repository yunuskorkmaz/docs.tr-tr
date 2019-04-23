---
title: ToolTip Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 3fbe883501d1ce36ca25ea07631f98042f451e07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197314"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> bileşen, kullanıcı denetimleri işaret ettiğinde metin görüntüler. Bir araç ipucu, herhangi bir denetimle ilişkili olabilir. Bu bileşen örnek kullanımını: bir form üzerinde alandan kazanmak için küçük bir simge çubuğunda görüntüleyebilir ve düğmenin işlevi açıklamak için bir araç ipucu kullanın.  
  
## <a name="working-with-the-tooltip-component"></a>ToolTip bileşeni ile çalışma  
 A <xref:System.Windows.Forms.ToolTip> bileşeni sağlar bir `ToolTip` özelliğini bir Windows Form veya diğer kapsayıcı birden çok denetim. Örneğin, bir yerleştirirseniz <xref:System.Windows.Forms.ToolTip> bileşen bir form üzerinde "adını buraya yazın" görüntüleyebilirsiniz bir <xref:System.Windows.Forms.TextBox> denetlemek ve "değişiklikleri kaydetmek için buraya tıklayın" bir <xref:System.Windows.Forms.Button> denetimi.  
  
 Anahtar yöntemlerini <xref:System.Windows.Forms.ToolTip> bileşenidir <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> ve <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Kullanabileceğiniz <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> görüntülenen denetimler için ToolTips ayarlama yöntemi. Daha fazla bilgi için [nasıl yapılır: Denetimler için ToolTips ayarlama bir Windows formunda tasarım zamanında](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Anahtar özellikleri <xref:System.Windows.Forms.ToolTip.Active%2A>, hangi ayarlanmalıdır `true` görünmesi araç ipucu için ve <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, araç ipucu dize gösterilen sürenin uzunluğunu ayarlar, ne kadar süreyle kullanıcı işaret etmelidir denetim görünmesi araç ipucu için ve onu uzun Sonraki araç ipucu windows görünmesini alır. Daha fazla bilgi için [nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolTip>
- [Nasıl yapılır: Tasarım zamanında bir Windows formundaki denetimler için ToolTips ayarlama](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
