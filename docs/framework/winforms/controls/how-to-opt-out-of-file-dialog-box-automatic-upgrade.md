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
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976889"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme
<xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları bir uygulamada kullanıldığında, görünümü ve davranışı uygulamanın üzerinde çalıştığı Windows sürümüne bağlıdır. .NET Framework 2,0 veya önceki bir sürümde oluşturulan bir uygulama Windows Vista 'da görüntüleniyorsa, <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> otomatik olarak Windows Vista görünümü ve davranışıyla birlikte görüntülenir. .NET Framework 3,0 ' den başlayarak, <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> [!INCLUDE[winxp](../../../../includes/winxp-md.md)]stili bir görünüm ve davranışla birlikte göstermek için otomatik yükseltmeyi devre dışı bırakabilirsiniz.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Dosya iletişim kutusu otomatik yükseltmeyi devre dışı bırakmak için  
  
1. İletişim kutusunu görüntülemeden önce <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliğini `false` olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FileDialog>
