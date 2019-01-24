---
title: Windows Forms Veri Bağlamada Bildirimi Değiştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 533bda1e08d2ed7d15160318e75f2c1b7224d989
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505906"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Forms Veri Bağlamada Bildirimi Değiştirme
Bir Windows Forms veri bağlamanın en önemli kavramları *bildirimi değiştirme*. Bağlama denetimleri ve veri kaynağı her zaman en son veri sağlamak için veri bağlama için değişiklik bildirimi eklemeniz gerekir. Özellikle ilişkili denetimler, veri kaynağına yapılan değişikliklerin bildirilmesini güvence altına almak istediğiniz ve veri kaynağına bağlı bir denetim özelliklerine yapılan değişiklikler, bildirilir.  
  
 Veri bağlama türüne bağlı olarak değişiklik bildirimi farklı tür vardır:  
  
-   Basit bağlama, bir tek denetim özelliği tek bir nesnenin örneğine bağlanır.  
  
-   Listedeki bir öğeye özelliğini veya bir denetim özelliği bağlı bir tek bir denetim özelliği liste tabanlı bağlama nesnelerin listesine bağlı.  
  
 Ayrıca, veri bağlama için kullanmak istediğiniz Windows Forms denetimleri oluşturuyorsanız uygulamalısınız *PropertyName*için bağlı bir denetim özelliğini değişiklikleri yayılana böylece deseni denetimlere değiştirildi veri kaynağı.  
  
## <a name="change-notification-for-simple-binding"></a>Basit bir bağlama için değişiklik bildirimi  
 İlişkili özelliğin değeri değiştiğinde basit bağlama için değişiklik bildirimi iş nesneleri sağlamanız gerekir. Oluşturarak bunu yapabilirsiniz bir *PropertyName*iş nesnenizin ve iş nesnesi ile denetimlere bağlama her bir özellik için değiştirilen olay <xref:System.Windows.Forms.BindingSource> veya iş nesnenizin uygulayan tercih edilen yöntemi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve harekete geçirirse bir <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> özelliğinin değeri değiştiğinde bir olay. Daha fazla bilgi için [nasıl yapılır: INotifyPropertyChanged arabirimini uygulama](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Uygulayan nesneler kullandığınızda <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi sahip olmadığınız kullanılacak <xref:System.Windows.Forms.BindingSource> nesneyi bir denetime bağlamak için ancak kullanarak <xref:System.Windows.Forms.BindingSource> önerilir.  
  
## <a name="change-notification-for-list-based-binding"></a>Liste tabanlı bağlamada bildirimi değiştirme  
 Windows Forms bağlıdır (liste öğesi özelliğinin değeri değiştirir) özellik değişikliğini sağlamak için bağlı bir liste ve liste değiştirildi (bir öğe silinmiş veya listesine) denetimleri bağlı bilgileri. Bu nedenle, veri bağlama için kullanılan listeleri uygulamalıdır <xref:System.ComponentModel.IBindingList>, her iki tür değişiklik bildirimi sağlar. <xref:System.ComponentModel.BindingList%601> Genel bir uygulamasıdır <xref:System.ComponentModel.IBindingList> ve Windows Forms veri bağlama ile kullanılmak üzere tasarlanmıştır. Oluşturabileceğiniz bir <xref:System.ComponentModel.BindingList%601> uygulayan bir iş nesnesi türü içeren <xref:System.ComponentModel.INotifyPropertyChanged> listesi otomatik olarak dönüştürülecektir <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayları <xref:System.ComponentModel.IBindingList.ListChanged> olayları. Bağlı bir liste ise bir <xref:System.ComponentModel.IBindingList>, nesnelerin listesini kullanarak Windows Forms denetimlerine bağlama gerekir <xref:System.Windows.Forms.BindingSource> bileşeni. <xref:System.Windows.Forms.BindingSource> Bileşeni özellik listesi dönüştürme benzer sağlayacağı <xref:System.ComponentModel.BindingList%601>. Daha fazla bilgi için [nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri yükseltmek](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Özel denetimler için değişiklik bildirimi  
 Denetim taraftan, son olarak ortaya koymalıdır bir *PropertyName*verilere bağlı için tasarlanmış her bir özellik için değiştirilen olay. Denetim özelliği değişiklikleri daha sonra bağlı veri kaynağına yayılır. Daha fazla bilgi için [nasıl yapılır: PropertyNameChanged desenini uygulama](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)
- [Windows Forms Tarafından Desteklenen Veri Kaynakları](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)
- [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
