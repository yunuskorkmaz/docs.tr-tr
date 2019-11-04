---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459097"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Nasıl yapılır: bağlamanın yönünü belirtme

Bu örnek, bağlamanın yalnızca bağlama hedefi (hedef) özelliğini, bağlama kaynağını (kaynak) özelliğini veya hem hedef özelliği hem de kaynak özelliğini güncelleştirip güncelleştirmediğini nasıl belirtmeyeceğinizi gösterir.  
  
## <a name="example"></a>Örnek  
 Bağlamanın yönünü belirtmek için <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> özelliğini kullanın. Güncelleştirmeleri bağlamaya yönelik kullanılabilen seçenekler şunlardır:  
  
- hedef özellik veya kaynak özelliği değiştiğinde <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> hedef özelliği ya da özelliğini güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>, hedef özelliği yalnızca kaynak özelliği değiştiğinde güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>, hedef özelliği yalnızca uygulama başladığında veya <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında güncelleştirir.  
  
- hedef özelliği değiştiğinde, kaynak özelliğini güncelleştirir <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>, hedef özelliğin varsayılan <xref:System.Windows.Data.Binding.Mode%2A> değerinin kullanılmasına neden olur.  
  
 Daha fazla bilgi için <xref:System.Windows.Data.BindingMode> sabit listesine bakın.  
  
 Aşağıdaki örnekte <xref:System.Windows.Data.Binding.Mode%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Kaynak değişikliklerini (<xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynağın <xref:System.ComponentModel.INotifyPropertyChanged>gibi uygun bir özellik değişim bildirimi mekanizması uygulaması gerekir. Bkz. <xref:System.ComponentModel.INotifyPropertyChanged> bir uygulama örneği için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) .  
  
 <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğini ayarlayarak kaynak güncelleştirmelerinin zamanlamasını kontrol edebilirsiniz. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
