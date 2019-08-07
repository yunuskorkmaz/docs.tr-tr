---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817916"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Nasıl yapılır: Bağlamanın yönünü belirtin

Bu örnek, bağlamanın yalnızca bağlama hedefi (hedef) özelliğini, bağlama kaynağını (kaynak) özelliğini veya hem hedef özelliği hem de kaynak özelliğini güncelleştirip güncelleştirmediğini nasıl belirtmeyeceğinizi gösterir.  
  
## <a name="example"></a>Örnek  
 Bağlamanın yönünü belirtmek <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> için özelliğini kullanın. Güncelleştirmeleri bağlamaya yönelik kullanılabilen seçenekler şunlardır:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>Target özelliği ya da Source özelliği değiştiğinde Target özelliğini veya özelliğini güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>hedef özelliği yalnızca kaynak özelliği değiştiğinde güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>hedef özelliği yalnızca uygulama başladığında veya <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>Target özelliği değiştiğinde kaynak özelliğini güncelleştirir.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>hedef özelliğin varsayılan <xref:System.Windows.Data.Binding.Mode%2A> değerinin kullanılmasına neden olur.  
  
 Daha fazla bilgi için bkz <xref:System.Windows.Data.BindingMode> . sabit listesi.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Data.Binding.Mode%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Kaynak değişiklikleri (ve <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynak gibi uygun bir özellik <xref:System.ComponentModel.INotifyPropertyChanged>değişikliği bildirim mekanizması gerçekleştirmelidir. Bkz. bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulama örneği için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) .  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları<xref:System.Windows.Data.BindingMode.OneWayToSource> için, özelliği ayarlayarak kaynak güncelleştirmelerinin zamanlamasını denetleyebilirsiniz. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
