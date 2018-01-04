---
title: "Windows Forms DataGridView Denetimindeki Varsayılan İşlevler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Varsayılan İşlevler
Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kullanıcılara bir miktarda varsayılan işlevsellik sağlar.  
  
## <a name="default-functionality"></a>Varsayılan işlevsellik  
 Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:  
  
-   Sütun üstbilgileri ve tablo dikey kayarken görünür kalmasını satır üstbilgilerinin otomatik olarak görüntüler.  
  
-   Geçerli satır için bir seçim gösterge içeren bir satır üstbilgisi vardır.  
  
-   Seçim dikdörtgeninin ilk hücreye sahiptir.  
  
-   Kullanıcı sütun Bölücü tıkladığında, otomatik olarak yeniden boyutlandırılabilir sütun içeriyor.  
  
-   Windows XP ve Windows Server 2003 ailesinin görsel stiller otomatik olarak destekler, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın çağrılır `Main` yöntemi.  
  
 Ayrıca, içeriğini bir <xref:System.Windows.Forms.DataGridView> denetim varsayılan olarak düzenlenebilir:  
  
-   Kullanıcı tıklattığında veya bir hücreye F2 bastığında, denetim otomatik olarak hücre düzenleme moduna geçirir ve hücre içeriğini kullanıcı türleri olarak güncelleştirir.  
  
-   Kullanıcı Kılavuzu sonuna kadar kaydırır, kullanıcının yeni kayıtları eklemek için bir satır var olduğunu görürsünüz. Kullanıcı bu satır tıkladığında, yeni bir satır eklenir <xref:System.Windows.Forms.DataGridView> varsayılan değerlerle denetim. Kullanıcı ESC tuşuna bastığında, bu yeni satır kaybolur.  
  
-   Satırda bir başlık kullanıcı tüm satırı seçilir.  
  
 Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetim ayarlayarak bir veri kaynağı için kendi <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği, denetimi:  
  
-   Otomatik olarak veri kaynağının sütunlarının adlarını sütunu üstbilgi metni olarak kullanır.  
  
-   Veri kaynağı içeriğiyle doldurulur. <xref:System.Windows.Forms.DataGridView>sütun, veri kaynağındaki her sütun için otomatik olarak oluşturulur.  
  
-   Görünür her satır için bir satır bir tablo oluşturur.  
  
-   Otomatik olarak kullanıcı bir sütun başlığını tıklattığında temel alınan verilere dayalı satırları sıralar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
