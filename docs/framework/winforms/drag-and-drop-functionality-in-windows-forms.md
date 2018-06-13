---
title: Windows Forms'ta Sürükle ve Bırak İşlevi
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: c43d5ad9203afad67601d9e36447db7c49a5a98e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539406"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Windows Forms'ta Sürükle ve Bırak İşlevi
Windows Forms bir yöntem, olayları ve sürükle ve bırak davranışı uygulayan sınıflar içerir. Bu konu Windows Forms'ta sürükle ve bırak desteği'ne genel bakış sağlar.  Ayrıca bkz. [sürükle ve bırak işlemleri ve Pano desteği](http://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).  
  
## <a name="performing-drag-and-drop-operations"></a>Sürükle ve bırak işlemleri gerçekleştirme  
 Sürükle ve bırak işlemi gerçekleştirmek için <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi <xref:System.Windows.Forms.Control> sınıfı. Sürükle ve bırak işlemi nasıl gerçekleştirildiğini hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Sürükle ve bırak işlemi başlamadan önce fare işaretçisini üzerine sürüklediğiniz gerekir dikdörtgen almak için <xref:System.Windows.Forms.SystemInformation.DragSize%2A> özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Sürükleme ve bırakma işlemleri için ilgili olayları  
 Sürükle ve bırak işlemi olayları iki kategorisi vardır: sürükle ve bırak işlemi geçerli hedefinde meydana gelen olayları ve sürükle ve bırak işlemi kaynak üzerinde meydana gelen olayları.  
  
### <a name="events-on-the-current-target"></a>Geçerli hedef olayları  
 Aşağıdaki tabloda bir Sürükle ve bırak işlemi geçerli hedefinde meydana gelen olayları gösterir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Bu olay, bir nesne denetimin sınırları sürüklendiğinde gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Bu olay, fare işaretçisini denetimin sınırları içinde olsa bir nesnesi sürüklenebilir oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Sürükle ve bırak işlemi tamamlandığında, bu olay oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Bu olay, bir nesne denetimin sınırların dışında sürüklendiğinde gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> Sınıfı, fare işaretçisini, fare düğmeleri geçerli durumunu ve değiştirici tuşlar, klavye, sürüklenen, veri konumunu sağlar ve <xref:System.Windows.Forms.DragDropEffects> sürükleme olay kaynağı tarafından izin verilen işlemler belirten değerleri ve işlem için hedef açılan etkisi.  
  
### <a name="events-on-the-source"></a>Olay kaynağı  
 Aşağıdaki tabloda sürükle ve bırak işlemi kaynak üzerinde meydana gelen olayları gösterir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Bu olay bir sürükleme işlemi sırasında oluşur. Fare işaretçisini değiştirmek gibi sürükle ve bırak işlemi gerçekleştirildiği kullanıcı görsel bir ipucu vermek için bir fırsat sunar. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Bu olay bir Sürükle ve bırak işlemi sırasında oluşturulur ve sürükle ve bırak işlemi iptal olup olmadığını belirlemek sürükleme kaynağı sağlar. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Sınıfı, düğmeler ve değiştirici tuşlar, klavye, ESC tuşuna basılı olup olmadığını belirten bir değeri fare geçerli durumunu sağlar ve bir <xref:System.Windows.Forms.DragAction> sürükle ve bırak işlemi devam etmesinin gerekip gerekmediğini belirlemek için ayarlanan değeri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
