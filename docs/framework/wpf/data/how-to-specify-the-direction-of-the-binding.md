---
title: "Nasıl yapılır: Bağlama Yönünü Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9944ff214a9dfe12b21e005c4e1998c249bf72b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Nasıl yapılır: Bağlama Yönünü Belirtme
Bu örnek, bağlama yalnızca bağlama target (hedef) özelliği, bağlama kaynağı (kaynak) özelliğine veya hedef özelliği hem kaynak özelliği güncelleştirmeleri olup olmadığını belirlemek gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Kullandığınız <xref:System.Windows.Data.Binding.Mode%2A> bağlama yönünü belirtmek için özellik. Aşağıdaki numaralandırma listesi bağlama güncelleştirmeleri için mevcut seçenekler gösterilmektedir:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>target özelliği ya da kaynak özelliği değiştiğinde hedef özelliği veya özelliği güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>target özelliği, yalnızca kaynak özelliği değiştiğinde güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime>target özelliği yalnızca uygulama başladığında veya güncelleştirmeleri <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>hedef özelliği değiştiğinde kaynak özelliğini güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.Default>Varsayılan neden <xref:System.Windows.Data.Binding.Mode%2A> kullanılacak hedef özelliğinin değeri.  
  
 Daha fazla bilgi için bkz: <xref:System.Windows.Data.BindingMode> numaralandırması.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Data.Binding.Mode%2A> özelliği.  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Kaynak değişikliklerini algılamak için (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirim mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>. Bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) ilişkin bir örnek bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.  
  
 İçin <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları ayarlayarak kaynak güncelleştirmelerinin zamanlamasını denetleyebilirsiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.Binding>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
