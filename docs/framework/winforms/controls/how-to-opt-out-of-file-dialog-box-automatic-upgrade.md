---
title: 'Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: a4be35617e8be1c6c83ac6f2d06e03b6cbb2977f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913671"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme
Zaman <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıflar, bir uygulamada kullanılıyorsa, üzerinde uygulamayı çalıştırdığınız Windows sürümü görünümlerini ve davranışlarını bağlıdır. Üzerinde oluşturulan uygulama [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] veya önceki görünür [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile otomatik olarak görüntülenen [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] görünümünü ve davranışını. İtibariyle [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], görüntülenecek otomatik yükseltmeyi iptal etme <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile bir [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-stil görünümünü ve davranışını.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Dosya iletişim kutusu otomatik yükseltmeyi iptal etme için  
  
1. Ayarlama <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> için `false` önce iletişim kutusunu görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FileDialog>
