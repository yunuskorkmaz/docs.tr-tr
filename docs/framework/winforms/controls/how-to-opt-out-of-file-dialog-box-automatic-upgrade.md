---
title: "Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b785b9da22aa6f17c14b85263b94fb70fbef5f7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme
Zaman <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları bir uygulamada kullanılan, üzerinde uygulamayı çalıştırdığınız Windows sürümü, Görünüm ve davranışlarını bağlıdır. Üzerinde oluşturulmuş uygulama [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ya da daha önce görüntülenen [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile otomatik olarak görüntülenen [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] Görünüm ve davranış. İtibariyle [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], görüntülemek için otomatik yükseltmeyi iptal et <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile bir [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-stil görünümünü ve davranışını.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Dosya iletişim kutusu otomatik yükseltmeyi iptal et için  
  
1.  Ayarlama <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> için `false` önce iletişim kutusunu görüntüleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FileDialog>
