---
title: "Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama
Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri hangisinin yalnızca biri atanabilir bir yordam veya nesne, iki veya daha fazla ayarları arasından seçim kullanıcılara vermek için tasarlanmıştır. Örneğin, bir grup <xref:System.Windows.Forms.RadioButton> denetimleri, sipariş paket hizmet sağlayıcılar seçimine görüntüleyebilir, ancak yalnızca bir hizmet sağlayıcılar kullanılır. Bu nedenle yalnızca bir <xref:System.Windows.Forms.RadioButton> işlevsel grubunun bir parçası olsa bile aynı anda seçilebilir.  
  
 İçinde bir kapsayıcı gibi çizerek radyo düğmesi grubunda bir <xref:System.Windows.Forms.Panel> denetimi, bir <xref:System.Windows.Forms.GroupBox> denetim ya da bir formu. Doğrudan bir form haline bir gruba eklenen tüm radyo düğmeleri. Ayrı grupları eklemek için bunları paneller veya grup kutuları içinde yerleştirmeniz gerekir. Panelleri veya grup kutuları hakkında daha fazla bilgi için bkz: [Panel denetimine genel bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) veya [GroupBox denetimine genel bakış](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>İşlev bağımsız olarak diğer ayarlar için bir küme olarak Grup RadioButton denetimlerini  
  
1.  Sürükleme bir <xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> gelen denetim **Windows Forms** sekmesi **araç** forma.  
  
2.  Çizim <xref:System.Windows.Forms.RadioButton> denetimlerini <xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RadioButton>  
 [RadioButton Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [Panel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [GroupBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [CheckBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [RadioButton Denetimi](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
