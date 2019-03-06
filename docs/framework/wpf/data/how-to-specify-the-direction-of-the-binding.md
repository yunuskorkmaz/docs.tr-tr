---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378229"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Nasıl yapılır: Bağlama Yönünü Belirtme
Bu örnek, bağlama yalnızca bağlama target (hedef) özelliği, bağlama (kaynak) kaynak özelliği veya hedef özelliği hem kaynak özelliği güncelleştirmeler olup olmadığını belirlemek nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Kullandığınız <xref:System.Windows.Data.Binding.Mode%2A> bağlama yönünü belirtme özelliği. Aşağıdaki numaralandırma listesi bağlama güncelleştirmeleri için mevcut seçenekler gösterilmektedir:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> hedef özelliği ya da kaynak özelliği değiştiğinde hedef özelliği veya özelliğini güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> yalnızca kaynak özelliği değiştiğinde hedef özelliğini güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> hedef özelliği yalnızca uygulama başladığında veya güncelleştirmeleri <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişiklik uygulanır.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> Hedef özelliği değiştiğinde kaynak özelliğini güncelleştirir.  
  
-   <xref:System.Windows.Data.BindingMode.Default> Varsayılan neden <xref:System.Windows.Data.Binding.Mode%2A> kullanılacak hedef özelliğinin değeri.  
  
 Daha fazla bilgi için <xref:System.Windows.Data.BindingMode> sabit listesi.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Data.Binding.Mode%2A> özelliği.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Kaynak değişikliklerini algılamak için (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirimi mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>. Bkz: [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) örneği için bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.  
  
 İçin <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları, kaynak güncelleştirmelerinin zamanlaması ayarlayarak denetleyebilirsiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
