---
title: DataGridView Denetimindeki varsayılan Işlevsellik
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746126"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Varsayılan İşlevler
Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi kullanıcılara önemli miktarda varsayılan işlevsellik sağlar.  
  
## <a name="default-functionality"></a>Varsayılan Işlevsellik  
 Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:  
  
- Tablo dikey olarak kaydırıldığında görünür kalan sütun üst bilgilerini ve satır üstbilgilerini otomatik olarak görüntüler.  
  
- Geçerli satır için seçim göstergesi içeren bir satır üst bilgisine sahiptir.  
  
- İlk hücrede seçim dikdörtgeni vardır.  
  
- Kullanıcı sütun bölücüleri çift tıkladığında otomatik olarak yeniden boyutlandırılabileceği sütunlar içerir.  
  
- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın `Main` yönteminden çağrıldığında Windows XP ve Windows Server 2003 ailesinden görsel stilleri otomatik olarak destekler.  
  
 Ayrıca, bir <xref:System.Windows.Forms.DataGridView> denetiminin içeriği varsayılan olarak düzenlenebilir:  
  
- Kullanıcı hücredeki F2 tuşuna çift tıkladığında veya basarsa, denetim hücreyi otomatik olarak düzenleme moduna geçirir ve hücrenin içeriğini Kullanıcı türleri olarak güncelleştirir.  
  
- Kullanıcı kılavuzun sonuna kaydığında, Kullanıcı yeni kayıt eklemek için bir satır bulunduğunu görür. Kullanıcı bu satıra tıkladığında, <xref:System.Windows.Forms.DataGridView> denetimine varsayılan değerlerle yeni bir satır eklenir. Kullanıcı ESC tuşuna bastığında bu yeni satır kaybolur.  
  
- Kullanıcı bir satır başlığına tıklarsa, satırın tamamı seçilir.  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlayarak bir <xref:System.Windows.Forms.DataGridView> denetimini bir veri kaynağına bağladığınızda denetim:  
  
- , Sütun üst bilgisi metni olarak veri kaynağının sütunlarının adlarını otomatik olarak kullanır.  
  
- Veri kaynağının içeriğiyle doldurulur. <xref:System.Windows.Forms.DataGridView> sütunları, veri kaynağındaki her bir sütun için otomatik olarak oluşturulur.  
  
- Tablodaki her bir görünür satır için bir satır oluşturur.  
  
- Kullanıcı bir sütun başlığına tıkladığında, temel alınan verilere göre satırları otomatik olarak sıralar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
