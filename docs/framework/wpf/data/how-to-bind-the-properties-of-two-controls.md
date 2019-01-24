---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 63584872c027ed3a80698304a7221c161c8d928a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570258"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Nasıl yapılır: İki Denetimin Özelliklerini Bağlama
Bu örnekte, başka bir örneği oluşturulan bir denetimin özellik bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Bu örnek oluşturulduğunda aşağıdaki gibi görünür:  
  
 ![Yeşil bir arka plana sahip bir tuval](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Not** bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır. Daha fazla bilgi için [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlama Kaynağı Belirtme](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
