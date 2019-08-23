---
title: 'Nasıl yapılır: PriorityBinding Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937441"
---
# <a name="how-to-implement-prioritybinding"></a>Nasıl yapılır: PriorityBinding Uygulama
<xref:System.Windows.Data.PriorityBinding>' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de bir bağlama listesi belirterek. Bağlamaların listesi, en yüksek öncelikten en düşük önceliğe göre sıralanır. En yüksek öncelikli bağlama işlendiğinde başarıyla bir değer döndürürse, listedeki diğer bağlamaları işlemeye hiçbir zaman gerek yoktur. En yüksek öncelikli bağlamanın değerlendirilmesi uzun zaman alacağından, daha yüksek bir öncelik bağlamasının bir değeri başarıyla döndürünceye kadar bir değer döndüren bir sonraki en yüksek öncelik kullanılır.  
  
## <a name="example"></a>Örnek  
 Nasıl <xref:System.Windows.Data.PriorityBinding> çalıştığını göstermek için `AsyncDataSource` , nesnesi aşağıdaki üç özelliklerle oluşturulmuştur: `FastDP`, `SlowerDP`ve `SlowestDP`.  
  
 Get erişimcisi `FastDP` , `_fastDP` veri üyesinin değerini döndürür.  
  
 Get erişimcisi `SlowerDP` , `_slowerDP` veri üyesinin değerini döndürmeden önce 3 saniye bekler.  
  
 Get erişimcisi `SlowestDP` , `_slowestDP` veri üyesinin değerini döndürmeden önce 5 saniye bekler.  
  
> [!NOTE]
> Bu örnek yalnızca tanıtım amaçlıdır. Yönergeler [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] , bir alan kümesinden daha yavaş büyüklüğü olan özellikleri tanımlamaya karşı önerilir. Daha fazla bilgi için bkz. [Özellikler ve yöntemler arasında seçim yapma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Özelliği `AsyncDS` kullanarak yukarıya<xref:System.Windows.Data.PriorityBinding>bağlar:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Bağlama altyapısı <xref:System.Windows.Data.Binding> nesneleri işlediğinde, `SlowestDP` özelliği ile <xref:System.Windows.Data.Binding>başlar, bu, özelliğe bağlanır. Bu işlendiğinde <xref:System.Windows.Data.Binding> , 5 saniye boyunca uymadığı için bir değeri başarıyla döndürmez, bu nedenle sonraki <xref:System.Windows.Data.Binding> öğe işlenir. Sonraki <xref:System.Windows.Data.Binding> bir değer, 3 saniye boyunca uyurken bir değeri başarıyla döndürmez. Bağlama altyapısı daha sonra <xref:System.Windows.Data.Binding> `FastDP` özelliğe bağlantılı olan bir sonraki öğeye gider. Bu <xref:System.Windows.Data.Binding> , "Fast Value" değerini döndürür. <xref:System.Windows.Controls.TextBlock> Şimdi "hızlı değer" değerini görüntüler.  
  
 3 saniye dolduktan sonra, `SlowerDP` özelliği "daha yavaş değer" değerini döndürür. <xref:System.Windows.Controls.TextBlock> Sonra "daha yavaş değer" değerini görüntüler.  
  
 5 saniye geçtikten sonra, `SlowestDP` özelliği "en yavaş değer" değerini döndürür. İlk olarak listelenen bu bağlama en yüksek önceliğe sahiptir. <xref:System.Windows.Controls.TextBlock> Şimdi "en yavaş değer" değerini görüntüler.  
  
 Bir <xref:System.Windows.Data.PriorityBinding> bağlamadan başarılı bir dönüş değeri olarak kabul edilen özellikler hakkında bilgi için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
