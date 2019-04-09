---
title: Windows Forms'ta Sürükle ve Bırak İşlevi
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 437b632706b27cd487d60c2ad23db3f9a3c96c09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108023"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Windows Forms'ta Sürükle ve Bırak İşlevi
Windows Forms, bir dizi yöntem, olayları ve sürükle-bırak davranışı uygulayan sınıflar içerir. Bu konu, Windows Forms'ta sürükle ve bırak desteği'ne genel bakış sağlar.  Ayrıca bkz: [sürükle ve bırak işlemleri ve Pano desteği](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Sürükle ve bırak işlemleri gerçekleştirme  
 Bir Sürükle ve bırak işlemi gerçekleştirmek için <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi <xref:System.Windows.Forms.Control> sınıfı. Bir Sürükle ve bırak işlemi nasıl gerçekleştirilir hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Bir Sürükle ve bırak işlemi başlamadan önce üzerinde fare işaretçisi sürüklenmelidir dikdörtgen almak için kullanın <xref:System.Windows.Forms.SystemInformation.DragSize%2A> özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Sürükle ve bırak işlemlerle ilgili olayları  
 Bir Sürükle ve bırak işlemi olayları iki kategorisi vardır: sürükle ve bırak işleminin geçerli hedef meydana gelen olayları ve sürükle ve bırak işlemi kaynağında meydana gelen olayları.  
  
### <a name="events-on-the-current-target"></a>Geçerli hedef olayları  
 Aşağıdaki tablo, bir Sürükle ve bırak işleminin geçerli hedef meydana gelen olayları gösterir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Bu olay, bir nesne denetimin sınırları içine sürüklendiğinde oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Bu olay, bir nesne fare işaretçisi denetimin sınırları içinde olsa da sürüklendiğinde oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Bu olay, bir Sürükle ve bırak işlemi tamamlandığında gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Bu olay, bir nesne denetimin sınırları dışında sürüklendiğinde oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> SAX fare düğmesi geçerli durumu ve değiştirici tuşlar sürüklenen, veri klavye, fare işaretçisi, konumunu ve <xref:System.Windows.Forms.DragDropEffects> Sürükle olayının kaynağı tarafından izin verilen işlemleri belirten değerleri ve işlemi için hedef bırakma efekti.  
  
### <a name="events-on-the-source"></a>Kaynak olayları  
 Aşağıdaki tabloda kaynak sürükle ve bırak işleminin meydana gelen olayları gösterir.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Bu olay bir sürükleme işlemi sırasında oluşur. Bu, sürükle ve bırak işlemi oluştuğunu, fare işaretçisini değiştirme gibi kullanıcı görsel bir ipucu vermek için bir fırsat sağlar. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Bu olay, bir Sürükle ve bırak işlemi sırasında oluşturulur ve sürükle ve bırak işleminin iptal edilip edilmeyeceğini belirlemek sürükleme kaynağı sağlar. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Sınıfı, düğmeler ve klavye, ESC tuşuna basılan tuşun olup olmadığını belirten bir değer değiştirici tuşları fare geçerli durumunu sağlar ve bir <xref:System.Windows.Forms.DragAction> sürükle ve bırak işlemi devam olup olmadığını belirlemek için ayarlanan değer.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
