---
title: 'Nasıl yapılır: PriorityBinding Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: a7729ec3d06ec701cf2194bed5d90b5bed76573a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037756"
---
# <a name="how-to-implement-prioritybinding"></a>Nasıl yapılır: PriorityBinding Uygulama
<xref:System.Windows.Data.PriorityBinding> içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağlamaları listesi belirterek çalışır. Bağlamaları listesi en düşük önceliği en yüksek öncelik aralığı sıralanır. En yüksek öncelikli bağlama bir değer döndürürse başarıyla işlendiğinde yoktur hiçbir zaman listedeki diğer bağlamalar işlem gerekmez. En yüksek öncelikli bağlama uyumluluğunun değerlendirilebilmesi için çok uzun sürüyor durumu olabilir, başarıyla bir değer döndüren bir sonraki en yüksek öncelikli bir daha yüksek bir öncelik değeri başarıyla döndürünceye kadar kullanılır.  
  
## <a name="example"></a>Örnek  
 Göstermek için nasıl <xref:System.Windows.Data.PriorityBinding> çalıştığını `AsyncDataSource` nesnesi şu üç özellik ile oluşturuldu: `FastDP`, `SlowerDP`, ve `SlowestDP`.  
  
 Get erişimcisine `FastDP` değerini döndürür `_fastDP` veri üyesi.  
  
 Get erişimcisine `SlowerDP` değerini döndürmeden önce 3 saniye bekler `_slowerDP` veri üyesi.  
  
 Get erişimcisine `SlowestDP` değerini döndürmeden önce 5 saniye bekler `_slowestDP` veri üyesi.  
  
> [!NOTE]
>  Bu örnek yalnızca gösterim amaçlıdır. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Kat bir alan kümesi olandan daha yavaş olan özellikleri tanımlamaya karşı önerir. Daha fazla bilgi için [NIB: seçme arasında özellikleri ve yöntemleri](https://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Özelliğine bağlayan yukarıdaki `AsyncDS` kullanarak <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Bağlama altyapısı işlediğinde <xref:System.Windows.Data.Binding> nesneler, ilk başladıktan <xref:System.Windows.Data.Binding>, bağlı `SlowestDP` özelliği. Olduğunda bu <xref:System.Windows.Data.Binding> olduğundan, 5 saniye için bu nedenle sonraki uyku için işlenen, bir değer başarıyla dönmez <xref:System.Windows.Data.Binding> öğesi işlenir. Sonraki <xref:System.Windows.Data.Binding> 3 saniye için uyku için bir değer başarıyla döndürmez. Bağlama altyapısı ardından sonraki taşır <xref:System.Windows.Data.Binding> bağlı öğe, `FastDP` özelliği. Bu <xref:System.Windows.Data.Binding> "Hızlı Value" değeri döndürür. <xref:System.Windows.Controls.TextBlock> Artık "Hızlı Value" değeri görüntüler.  
  
 3 saniye geçtikten sonra `SlowerDP` özelliği "Daha yavaş Value" değeri döndürür. <xref:System.Windows.Controls.TextBlock> "Daha yavaş value" değerini görüntüler.  
  
 5 saniye geçtikten sonra `SlowestDP` özelliği, "En yavaş Value" değeri döndürür. Bu bağlama, ilk listelenmediğinden en yüksek önceliğe sahip. <xref:System.Windows.Controls.TextBlock> Artık "yavaş value" görüntüler.  
  
 Bkz: <xref:System.Windows.Data.PriorityBinding> bağlamadan başarılı bir dönüş değeri olarak kabul hakkında bilgi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
