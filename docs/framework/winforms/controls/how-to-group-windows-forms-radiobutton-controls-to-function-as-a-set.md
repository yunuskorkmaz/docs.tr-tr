---
title: Grup RadioButton denetimlerini küme olarak çalışacak şekilde grupla
description: Windows Forms RadioButton denetimlerini diğer kümelerden bağımsız olarak çalışacak şekilde nasıl grupleyeceğinizi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325928"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama
Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri, kullanıcılara iki veya daha fazla ayar arasında seçim yapmak üzere tasarlanmıştır. Bu, bir yordama veya nesneye yalnızca bir tane atanabilir. Örneğin, bir Grup denetim, bir <xref:System.Windows.Forms.RadioButton> sipariş için paket taşıyıcılar seçimi gösterebilir, ancak yalnızca bir tane taşıyıcılar kullanılır. Bu nedenle <xref:System.Windows.Forms.RadioButton> , bir işlevsel grubun parçası olsa bile tek seferde yalnızca bir tane seçilebilir.  
  
 Radyo düğmelerini <xref:System.Windows.Forms.Panel> Denetim, denetim veya form gibi bir kapsayıcının içine çizerek gruplandırabilirsiniz <xref:System.Windows.Forms.GroupBox> . Doğrudan bir forma eklenen tüm radyo düğmeleri tek bir grup haline gelir. Ayrı gruplar eklemek için bunları panellerin veya grup kutularının içine yerleştirmeniz gerekir. Paneller veya Grup kutuları hakkında daha fazla bilgi için bkz. [panel denetimine genel bakış](panel-control-overview-windows-forms.md) veya [GroupBox denetimine genel bakış](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>RadioButton denetimlerini diğer kümelerden bağımsız olarak çalışacak şekilde gruplandırmak için  
  
1. <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> **Araç kutusundaki** **Windows Forms** sekmesinden bir veya denetimini form üzerine sürükleyin.  
  
2. <xref:System.Windows.Forms.RadioButton>Veya denetiminde denetimler çizin <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton Denetimine Genel Bakış](radiobutton-control-overview-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [GroupBox Denetimine Genel Bakış](groupbox-control-overview-windows-forms.md)
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [RadioButton Denetimi](radiobutton-control-windows-forms.md)
