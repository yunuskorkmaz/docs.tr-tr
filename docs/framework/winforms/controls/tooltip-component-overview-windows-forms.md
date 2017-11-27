---
title: "ToolTip Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> bileşen kullanıcı denetimleri işaret ettiğinde metin görüntüler. Bir araç ipucu herhangi bir denetimle ilişkili olabilir. Bu bileşen örnek kullanımını: bir form üzerinde alanı kaydetmek için küçük bir simge bir düğme görüntüleyebilir ve düğmenin işlevi açıklamak için bir araç ipucunu kullanın.  
  
## <a name="working-with-the-tooltip-component"></a>ToolTip bileşeni ile çalışma  
 A <xref:System.Windows.Forms.ToolTip> bileşen sağlayan bir `ToolTip` denetimlere birden çok Windows Form veya diğer kapsayıcı özelliği. Örneğin, biri yerleştirileceği <xref:System.Windows.Forms.ToolTip> bileşen bir form üzerinde "adını buraya yazın" görüntüleyebilir bir <xref:System.Windows.Forms.TextBox> denetlemek ve "değişiklikleri kaydetmek için burayı tıklatın" bir <xref:System.Windows.Forms.Button> denetim.  
  
 Anahtar yöntemleri <xref:System.Windows.Forms.ToolTip> bileşeni olan <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> ve <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Kullanabileceğiniz <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> görüntülenen denetimler için araç ipuçları ayarlamak için yöntem. Daha fazla bilgi için bkz: [nasıl yapılır: tasarım zamanında Windows formundaki denetimler için araç ipuçları kümesi](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Anahtar Özellikler <xref:System.Windows.Forms.ToolTip.Active%2A>, hangi ayarlanmalıdır `true` görünmesi araç ipucu için ve <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, araç ipucu dize gösterilen süreyi ayarlar, ne kadar süreyle kullanıcı işaret etmelidir görünmesi araç ipucu denetimi sırasında ve onu uzun nasıl Sonraki araç ipucu windows görünmesi alır. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolTip>  
 [Nasıl yapılır: araç ipuçları bir Windows formundaki denetimler için tasarım zamanında ayarlama](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [Nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
