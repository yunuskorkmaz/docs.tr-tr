---
title: Windows Forms DataGridView Denetiminde Performans Ayarlaması
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 556e3f682b6b863f8ab350c1b8ca7409a04a94fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729044"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Performans Ayarlaması
Büyük miktarlarda verilerin çalışırken `DataGridView` dikkatle kullanmadığınız sürece, Denetim büyük miktarda bellek ek yüküne, kullanabilir. Sınırlı belleğe sahip istemciler üzerinde bu ek yükü bazıları maliyeti yüksek bir belleğe sahip özellikler önleyerek önleyebilirsiniz. Senaryonuz için bellek kullanımını özelleştirmek için sanal mod kullanarak kendiniz alma görevlerini ve bazılarını veya tümünü veri Bakımı de yönetebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Nasıl kullanılacağını açıklar `DataGridView` denetimi bir şekilde büyük miktarlarda veri ile çalışırken, gereksiz bellek kullanımını ve performansını yaptırımlara önler.  
  
 [Windows Forms DataGridView Denetiminde Sanal Mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Standart veri bağlama mekanizması değiştirmek veya desteklemek için sanal mod kullanmayı açıklar.  
  
 [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Birkaç sanal modu olayları için işleyiciler uygulanacağını açıklar. Ayrıca, satır düzeyi geri alma ve kullanıcı düzenlemeleri için değişiklikleri uygulamak nasıl gösterir.  
  
 [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Kullanılabilir istemci bellek depolayabilirsiniz daha görüntülemek için daha fazla veriniz olduğunda, kullanışlı olan isteğe bağlı olarak veri yükleme işlemini açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
