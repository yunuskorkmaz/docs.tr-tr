---
title: DataGridView denetiminde performans ayarlaması
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744267"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Performans Ayarlaması
Büyük miktarda verilerle çalışırken, dikkatli bir şekilde kullanmadığınız müddetçe `DataGridView` denetimi ek yük olarak büyük miktarda bellek tüketebilir. Sınırlı belleğe sahip istemcilerde, yüksek bellek maliyeti olan özelliklerden kaçınarak bu ek yükün bazılarını önleyebilirsiniz. Senaryonuza yönelik bellek kullanımını özelleştirmek için, sanal modu kullanarak veri bakım ve alma görevlerinin bazılarını veya tümünü de yönetebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 `DataGridView` denetiminin, büyük miktarlarda verilerle çalışırken gereksiz bellek kullanımını ve performans yaptırımlarını önleyen bir şekilde nasıl kullanılacağını açıklar.  
  
 [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Standart veri bağlama mekanizmasını tamamlamak veya değiştirmek için sanal modun nasıl kullanılacağını açıklar.  
  
 [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](implementing-virtual-mode-wf-datagridview-control.md)  
 Birkaç sanal mod olay için işleyicilerin nasıl uygulanacağını açıklar. Ayrıca, Kullanıcı düzenlemeleri için satır düzeyinde geri alma ve işlemeye nasıl uygulanacağını gösterir.  
  
 [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Kullanılabilir istemci belleğinin depolayabileceğinden daha fazla veriniz olduğunda yararlı olan verileri isteğe bağlı olarak nasıl yükleyebileceğinizi açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği için başvuru belgeleri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
