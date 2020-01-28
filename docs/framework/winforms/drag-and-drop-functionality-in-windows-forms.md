---
title: Sürükle ve bırak Işlevi
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 603dc158719c0b11def4386eb24a33f235cf3a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732749"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Windows Forms'ta Sürükle ve Bırak İşlevi
Windows Forms, sürükle ve bırak davranışını uygulayan bir Yöntemler, olaylar ve sınıflar kümesi içerir. Bu konu, Windows Forms ' de sürükle ve bırak desteğine genel bir bakış sağlar.  Ayrıca bkz. [sürükle ve bırak işlemleri ve Pano desteği](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Sürükle ve bırak Işlemleri gerçekleştirme  
 Bir sürükle ve bırak işlemi gerçekleştirmek için <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemini kullanın. Bir sürükle ve bırak işleminin nasıl gerçekleştirildiği hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Bir sürükle ve bırak işlemi başlamadan önce fare işaretçisinin üzerine sürüklenmesi gereken dikdörtgeni almak için <xref:System.Windows.Forms.SystemInformation> sınıfının <xref:System.Windows.Forms.SystemInformation.DragSize%2A> özelliğini kullanın.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Sürükle ve bırak Işlemleriyle Ilgili olaylar  
 Sürükle ve bırak işleminde iki olay kategorisi vardır: sürükle ve bırak işleminin geçerli hedefinde gerçekleşen olaylar ve sürükle ve bırak işleminin kaynağında gerçekleşen olaylar.  
  
### <a name="events-on-the-current-target"></a>Geçerli hedefteki olaylar  
 Aşağıdaki tabloda, sürükle ve bırak işleminin geçerli hedefinde gerçekleşen olaylar gösterilmektedir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Bu olay, bir nesne denetimin sınırlarına sürüklendiğinde oluşur. Bu olay için işleyici <xref:System.Windows.Forms.DragEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.DragOver>|Bu olay, fare işaretçisi denetimin sınırları içinde olduğunda bir nesne sürüklendiğinde oluşur. Bu olay için işleyici <xref:System.Windows.Forms.DragEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Bu olay, bir sürükle ve bırak işlemi tamamlandığında oluşur. Bu olay için işleyici <xref:System.Windows.Forms.DragEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Bu olay, bir nesne denetimin sınırları dışına sürüklendiğinde oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır.|  
  
 <xref:System.Windows.Forms.DragEventArgs> sınıfı, fare işaretçisinin konumunu, klavye için fare düğmelerinin ve değiştirici tuşlarının, <xref:System.Windows.Forms.DragDropEffects> sürüklenen verilerin ve sürükleme olayının kaynağı tarafından izin verilen işlemleri belirten değerleri ve işlem için hedef bırakma efektini sağlar.  
  
### <a name="events-on-the-source"></a>Kaynaktaki olaylar  
 Aşağıdaki tabloda, sürükle ve bırak işleminin kaynağında gerçekleşen olaylar gösterilmektedir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Bu olay, bir sürükleme işlemi sırasında oluşur. Kullanıcıya, fare işaretçisini değiştirme gibi sürükle ve bırak işleminin gerçekleştiğini gösteren görsel bir yardım veren bir fırsat sağlar. Bu olay için işleyici <xref:System.Windows.Forms.GiveFeedbackEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Bu olay bir sürükle ve bırak işlemi sırasında oluşturulur ve sürükle ve bırak işleminin iptal edilip edilmeyeceğini anlamak için Sürükle kaynağını sağlar. Bu olay için işleyici <xref:System.Windows.Forms.QueryContinueDragEventArgs>türünde bir bağımsız değişken alır.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> sınıfı, klavye için fare düğmelerinin ve değiştirici tuşlarının geçerli durumunu, ESC tuşuna basıldığını belirten bir değeri ve sürükle ve bırak işleminin devam edip etmediğini belirlemek üzere ayarlanabilir bir <xref:System.Windows.Forms.DragAction> değeri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
