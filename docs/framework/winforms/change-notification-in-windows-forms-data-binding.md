---
title: "Windows Forms Veri Bağlamada Bildirimi Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffafaff2355e89e2127742f2fba5c005492b4580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Forms Veri Bağlamada Bildirimi Değiştirme
Windows Forms veri bağlama en önemli kavramlarını biri *bildirimi değiştirme*. Veri kaynağı ve ilişkili denetimler her zaman en yeni verilere sahip olduğunuzdan emin olmak için veri bağlama için değişiklik bildirimi eklemeniz gerekir. Özellikle, kendi veri kaynağına yapılan değişiklikler, ilişkili denetimler bildirilir olmak istiyorsanız ve veri kaynağı bir denetim ilişkili özelliklerine yapılan değişiklikler, bildirim.  
  
 Veri bağlama türüne bağlı olarak değişiklik bildirimi farklı türleri şunlardır:  
  
-   Tek denetim özelliğini tek bir nesnenin örneğine bağlı basit bağlama.  
  
-   Listedeki bir öğeye özelliğinin veya denetim özelliğini bağlı tek bir denetim özelliği liste tabanlı bağlama nesneler listesine bağlı.  
  
 Ayrıca, veri bağlama için kullanmak istediğiniz Windows Forms denetimleri oluşturuyorsanız uygulamalısınız *PropertyName*böylece bir denetim bağlı özelliğini değişiklikleri için yayılır düzeni denetimlere değiştirildi veri kaynağı.  
  
## <a name="change-notification-for-simple-binding"></a>Basit bağlama için değişiklik bildirimi  
 İlişkili özelliğin değeri değiştiğinde basit bağlama için değişiklik bildirimi iş nesneleri sağlamanız gerekir. Bunu göstererek yapmak bir *PropertyName*değiştirilen olay iş nesnesi ve iş nesnesi ile denetimlere bağlama her bir özellik için <xref:System.Windows.Forms.BindingSource> veya business nesnenizin uygulayan tercih edilen yöntemi <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve başlatır bir <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bir özellik değeri değiştiğinde olay. Daha fazla bilgi için bkz: [nasıl yapılır: INotifyPropertyChanged arabirimini uygulama](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Uygulayan nesneler kullandığınızda <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi, sahip olmadığınız kullanmak <xref:System.Windows.Forms.BindingSource> denetime nesneyi bağlamak için ancak kullanarak <xref:System.Windows.Forms.BindingSource> önerilir.  
  
## <a name="change-notification-for-list-based-binding"></a>Liste tabanlı bağlama için değişiklik bildirimi  
 Windows Forms bağlıdır (bir liste öğesi özelliği değeri değişir) özellik değişikliği sağlamak için ilişkili bir liste ve liste değiştirildi (öğeyi silinmiş ya da listeye eklenen) bağlama denetimleri için bilgi. Bu nedenle, veri bağlama için kullanılan listeleri uygulamalıdır <xref:System.ComponentModel.IBindingList>, her iki tür değişiklik bildirimi sağlar. <xref:System.ComponentModel.BindingList%601> Genel uygulamasıdır <xref:System.ComponentModel.IBindingList> ve Windows Forms veri bağlama ile kullanılmak üzere tasarlanmıştır. Oluşturabileceğiniz bir <xref:System.ComponentModel.BindingList%601> uygulayan bir iş nesnesi türü içeren <xref:System.ComponentModel.INotifyPropertyChanged> ve listesini otomatik olarak dönüştürmek <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayları <xref:System.ComponentModel.IBindingList.ListChanged> olaylar. Bağımlı liste değilse bir <xref:System.ComponentModel.IBindingList>, nesnelerin listesini kullanarak Windows Forms denetimlerine bağlamanız gerekir <xref:System.Windows.Forms.BindingSource> bileşeni. <xref:System.Windows.Forms.BindingSource> Bileşen özellik listesi dönüştürme benzer sağlayacaktır <xref:System.ComponentModel.BindingList%601>. Daha fazla bilgi için bkz: [nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Özel denetimler için değişiklik bildirimi  
 Son olarak, Denetim taraftan, kullanıma sunmak gerekir bir *PropertyName*değiştirilen olay verileri bağlanması için tasarlanmış her bir özellik için. Denetim özelliği değişiklikleri daha sonra bağlı veri kaynağına yayılır. Daha fazla bilgi için bkz: [nasıl yapılır: PropertyNameChanged desenini uygulama](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Windows Forms veri bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows Forms tarafından desteklenen veri kaynakları](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Veri bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
