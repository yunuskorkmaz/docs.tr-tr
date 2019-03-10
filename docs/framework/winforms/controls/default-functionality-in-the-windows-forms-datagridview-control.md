---
title: Windows Forms DataGridView Denetimindeki Varsayılan İşlevler
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 0c0d24111a2fdf856ff1f4ce154ec85afbbd61ee
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719669"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Varsayılan İşlevler
Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi varsayılan işlevselliği önemli ölçüde ile kullanıcılara sağlar.  
  
## <a name="default-functionality"></a>Varsayılan işlevsellik  
 Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:  
  
-   Sütun üst bilgilerini ve tablo dikey kaydırma yaparken görünür kalmasını satır üst bilgileri otomatik olarak görüntüler.  
  
-   Seçimi göstergesi geçerli satır içeren bir satır üst bilgisi yok.  
  
-   Seçim dikdörtgeninin ilk hücreye sahiptir.  
  
-   Sütun ayırıcılarını kullanıcı çift tıkladığında, otomatik olarak yeniden boyutlandırılıp boyutlandırılamayacağını sütun içeriyor.  
  
-   Görsel stiller, Windows XP ve Windows Server 2003 ailesinde otomatik olarak destekler, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın çağrılır `Main` yöntemi.  
  
 Ayrıca, içeriğini bir <xref:System.Windows.Forms.DataGridView> denetim varsayılan olarak düzenlenebilir:  
  
-   Kullanıcı çift tıklamaları birbirinden ayırma ya da bir hücreye F2 tuşuna basar denetimi otomatik olarak hücre düzenleme moduna geçirir ve hücre içeriğini kullanıcı türleri olarak güncelleştirir.  
  
-   Kullanıcı Kılavuzu sonuna kadar kaydırma ise kullanıcı yeni kayıtları eklemek için bir satır bulunduğunu görürsünüz. Kullanıcı bu satırı tıkladığında, yeni bir satır eklenir <xref:System.Windows.Forms.DataGridView> denetimiyle varsayılan değerleri. Bu yeni satır, kullanıcı ESC tuşuna bastığında kaybolur.  
  
-   Kullanıcı bir satır üst bilgisi tıklarsa, tüm satırı seçilir.  
  
 Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetim ayarlayarak bir veri kaynağı için kendi <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği, denetimi:  
  
-   Otomatik olarak veri kaynağının sütunlarının adlarını, sütun üst bilgi metni olarak kullanır.  
  
-   Veri kaynağının içeriğiyle doldurulur. <xref:System.Windows.Forms.DataGridView> sütunlar, veri kaynağındaki her sütun için otomatik olarak oluşturulur.  
  
-   Görünür her satır için bir satır bir tablo oluşturur.  
  
-   Kullanıcı bir sütun başlığına sağ tıkladığında, temel alınan verileri temel alan satır otomatik olarak sıralar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
