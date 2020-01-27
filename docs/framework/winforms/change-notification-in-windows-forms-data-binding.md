---
title: Veri bağlamada değişiklik bildirimi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746351"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Forms Veri Bağlamada Bildirimi Değiştirme
Windows Forms veri bağlamasının en önemli kavramlarından biri *değişiklik bildirimi*'dir. Veri kaynağınız ve bağlama denetimlerinizin en son verileri her zaman aldığından emin olmak için veri bağlama için değişiklik bildirimi eklemeniz gerekir. Özellikle, bağlantılı denetimlerin veri kaynaklarına yapılan değişiklikler hakkında bilgilendirilmek ve veri kaynağına bir denetimin ilişkili özelliklerinde yapılan değişiklikler hakkında bildirim gönderilmesini sağlamak istersiniz.  
  
 Veri bağlamanın türüne bağlı olarak farklı türlerde değişiklik bildirimi vardır:  
  
- Tek bir denetim özelliğinin bir nesnenin tek bir örneğine bağlandığı basit bağlama.  
  
- Liste tabanlı bağlama, bir listedeki bir öğenin özelliğine veya bir nesne listesine bağlı denetim özelliğine bağlı tek bir denetim özelliği içerebilir.  
  
 Ayrıca, veri bağlama için kullanmak istediğiniz Windows Forms denetimleri oluşturuyorsanız, denetimin bağlama özelliğindeki değişikliklerin veri kaynağına yayılması için, *PropertyName*değiştirilmiş deseninin denetimlere uygulanması gerekir.  
  
## <a name="change-notification-for-simple-binding"></a>Basit bağlama için değişiklik bildirimi  
 Basit bağlama için, bir ilişkili özelliğin değeri değiştiğinde iş nesnelerinin değişiklik bildirimi sağlaması gerekir. Bu, iş nesnenizin her bir özelliği için bir *PropertyName*Changed olayını kullanıma sunarak ve iş nesnesini <xref:System.Windows.Forms.BindingSource> veya iş nesnenizin <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayan ve bir özelliğin değeri değiştiğinde <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bir olay harekete geçiren bir yöntemi olan denetimlere bağlayarak yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: INotifyPropertyChanged arabirimini uygulama](how-to-implement-the-inotifypropertychanged-interface.md). <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayan nesneler kullandığınızda, nesneyi bir denetime bağlamak için <xref:System.Windows.Forms.BindingSource> kullanmanız gerekmez, ancak <xref:System.Windows.Forms.BindingSource> kullanılması önerilir.  
  
## <a name="change-notification-for-list-based-binding"></a>Liste tabanlı bağlama için değişiklik bildirimi  
 Windows Forms, özellik değişikliği (liste öğesi Özellik değeri değişiklikleri) ve liste değişti (bir öğe silinir veya listeye eklenir) bilgilerine bağlı denetimlere göre değişir. Bu nedenle, veri bağlama için kullanılan listelerin her iki tür değişiklik bildirimini sağlayan <xref:System.ComponentModel.IBindingList>uygulaması gerekir. <xref:System.ComponentModel.BindingList%601>, <xref:System.ComponentModel.IBindingList> genel bir uygulamasıdır ve Windows Forms veri bağlamasıyla kullanılmak üzere tasarlanmıştır. <xref:System.ComponentModel.INotifyPropertyChanged> uygulayan bir iş nesnesi türü içeren <xref:System.ComponentModel.BindingList%601> oluşturabilirsiniz ve liste, <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olaylarını otomatik olarak <xref:System.ComponentModel.IBindingList.ListChanged> olaylara dönüştürür. Bağlı liste bir <xref:System.ComponentModel.IBindingList>değilse, <xref:System.Windows.Forms.BindingSource> bileşenini kullanarak nesne listesini Windows Forms denetimlerine bağlamanız gerekir. <xref:System.Windows.Forms.BindingSource> bileşeni, <xref:System.ComponentModel.BindingList%601>şuna benzer şekilde özelliğe-listeye dönüştürme sağlayacak. Daha fazla bilgi için bkz. [nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri oluşturma](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Özel denetimler için değişiklik bildirimi  
 Son olarak, denetim tarafında, verilere bağlanacak şekilde tasarlanan her bir özellik için *PropertyName*Changed olayını kullanıma sunmalısınız. Denetim özelliğindeki değişiklikler daha sonra, bağlantılı veri kaynağına yayılır. Daha fazla bilgi için bkz [. nasıl yapılır: PropertyNameChanged modelini uygulama](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Windows Forms Tarafından Desteklenen Veri Kaynakları](data-sources-supported-by-windows-forms.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
