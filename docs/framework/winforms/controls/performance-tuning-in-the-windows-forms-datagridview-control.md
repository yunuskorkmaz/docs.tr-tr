---
title: "Windows Forms DataGridView Denetiminde Performans Ayarlaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Performans Ayarlaması
Büyük miktarlarda verilerin çalışırken `DataGridView` dikkatle kullanmadığınız sürece denetim çok miktarda ek yük, bellekte tüketebileceği. Sınırlı belleği olan istemciler üzerinde bu ek yükü bazıları maliyeti yüksek bellek sahip özellikleri kaçınarak önleyebilirsiniz. Senaryonuz için bellek kullanımını özelleştirmek için sanal modu kullanarak kendiniz alma görevleri ve bazılarını veya tümünü veri bakımı da yönetebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Nasıl kullanılacağını açıklar `DataGridView` , büyük miktarlarda veri çalışırken gereksiz bellek kullanımı ve performans cezaları önler şekilde denetim.  
  
 [Sanal mod Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Sanal mod tamamlayabilir veya standart veri bağlama mekanizması değiştirmek için nasıl kullanılacağını açıklar.  
  
 [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Birden fazla sanal modu olayları için işleyiciler uygulamak açıklar. Ayrıca satır düzeyi geri alma ve kullanıcı düzenlemeleri için yürütme uygulamak nasıl gösterir.  
  
 [Tam zamanında veri Windows Forms DataGridView denetiminde yükleme ile sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Kullanılabilir istemci bellek depolayabilir daha görüntülemek için daha fazla veri varsa, yararlı olan isteğe bağlı veri yükleme açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGridView denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows Forms DataGridView denetiminde veri görüntüleme modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
