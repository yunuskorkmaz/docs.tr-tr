---
title: "Windows Forms Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77f01bc462be67c3b613b8ab102a359a80d74140
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-data-binding"></a>Windows Forms Veri Bağlama
Windows Forms veri bağlama görüntülemek ve form üzerinde denetimleri içinde bir veri kaynağından bilgileri değişiklikler yapmak için araçlar sağlar. Hem geleneksel veri kaynakları yanı sıra veri içeren neredeyse her yapısı bağlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 Windows Forms veri bağlama genel bir bakış sağlar.  
  
 [Windows Forms Tarafından Desteklenen Veri Kaynakları](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 Windows Forms ile kullanılabilen veri kaynakları açıklar.  
  
 [Veri Bağlama ile İlgili Arabirimler](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 Windows Forms veri bağlama ile kullanılan arabirimlere bazıları açıklanmaktadır.  
  
 [Nasıl yapılır: Windows Forms’ta Verilerde Gezinme](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 Bir veri kaynağındaki öğeler arasında gezinmek gösterilmiştir.  
  
 [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 Windows Forms veri bağlama için değişiklik bildirimi farklı türleri açıklanmaktadır.  
  
 [Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 Nasıl uygulandığını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Arabirim ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerini iletişim kurar.  
  
 [Nasıl yapılır: PropertyNameChanged Desenini Uygulama](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 Nasıl uygulanacağını gösterir *PropertyName*bir Windows Forms kullanıcı denetimi özelliklerini değiştirilen deseni.  
  
 [Nasıl yapılır: ITypedList Arabirimini Uygulama](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 Uygulayarak bağlanabilirse listesi için şema bulunmasını etkinleştirmek gösterilmiştir <xref:System.ComponentModel.ITypedList> arabirimi.  
  
 [Nasıl yapılır: IListSource Arabirimini Uygulama](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 Nasıl uygulandığını gösterir <xref:System.ComponentModel.IListSource> bağlanabilirse sınıfı oluşturmak için arabirimi uygulamaz <xref:System.Collections.IList>, ancak başka bir konumdan bir liste sağlar.  
  
 [Nasıl yapılır: Aynı Veri Kaynağına Bağlanan Birden Çok Denetimin Eşitlenmiş Kalmasını Sağlama](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 Nasıl işleneceğini gösterir <xref:System.Windows.Forms.BindingSource.BindingComplete> olay veri kaynağı için ilişkili tüm denetimler eşitlenmiş kaldığından emin olun.  
  
 [Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 Üst tablo alanı için bir değişiklik yapıldığında, bir alt tabloda seçilen satırın değişmez emin olmak gösterilmiştir.  
  
 Ayrıca bkz. [arabirimleri ile ilgili veri bağlama](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [nasıl yapılır: Windows formlarında verilerde gezinme](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Bağlama bağlanabilirse bileşeni ve bir veri kaynağı arasındaki temsil eden sınıf açıklar.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Denetimlere bağlama için bir veri kaynağı yalıtır sınıfı tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [BindingSource Bileşeni](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 Nasıl kullanılacağını gösteren konuların listesi içeren <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
 [DataGridView Denetimi](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 Bağlanabilir datagrid denetimini nasıl kullanılacağını gösteren konuların listesini sağlar.  
  
 Ayrıca bkz. [Visual Studio'da verilere erişme](/visualstudio/data-tools/accessing-data-in-visual-studio).
