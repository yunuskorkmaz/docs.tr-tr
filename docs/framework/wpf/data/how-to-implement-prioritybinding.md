---
title: 'Nasıl yapılır: PriorityBinding Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459788"
---
# <a name="how-to-implement-prioritybinding"></a>Nasıl yapılır: PriorityBinding Uygulama
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Data.PriorityBinding>, bağlamaların bir listesini belirterek işe yarar. Bağlamaların listesi, en yüksek öncelikten en düşük önceliğe göre sıralanır. En yüksek öncelikli bağlama işlendiğinde başarıyla bir değer döndürürse, listedeki diğer bağlamaları işlemeye hiçbir zaman gerek yoktur. En yüksek öncelikli bağlamanın değerlendirilmesi uzun zaman alacağından, daha yüksek bir öncelik bağlamasının bir değeri başarıyla döndürünceye kadar bir değer döndüren bir sonraki en yüksek öncelik kullanılır.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Data.PriorityBinding> nasıl çalıştığını göstermek için, `AsyncDataSource` nesnesi şu üç özellik ile oluşturulmuştur: `FastDP`, `SlowerDP`ve `SlowestDP`.  
  
 `FastDP` get erişimcisi `_fastDP` veri üyesinin değerini döndürür.  
  
 `SlowerDP` get erişimcisi `_slowerDP` veri üyesinin değerini döndürmeden önce 3 saniye bekler.  
  
 `SlowestDP` get erişimcisi `_slowestDP` veri üyesinin değerini döndürmeden önce 5 saniye bekler.  
  
> [!NOTE]
> Bu örnek yalnızca tanıtım amaçlıdır. .NET yönergeleri, bir alan kümesinden daha yavaş büyüklüğü olan özellikleri tanımlamaya karşı önerilir. Daha fazla bilgi için bkz. [Özellikler ve yöntemler arasında seçim yapma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği, <xref:System.Windows.Data.PriorityBinding>kullanarak yukarıdaki `AsyncDS` bağlar:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Bağlama altyapısı <xref:System.Windows.Data.Binding> nesnelerini işlediğinde, `SlowestDP` özelliğine bağlantılı olan ilk <xref:System.Windows.Data.Binding>başlar. Bu <xref:System.Windows.Data.Binding> işlendiğinde, 5 saniye boyunca uymadığı için bir değeri başarıyla döndürmez, bu nedenle sonraki <xref:System.Windows.Data.Binding> öğesi işlenir. Sonraki <xref:System.Windows.Data.Binding>, 3 saniye boyunca uyduğundan bir değeri başarıyla döndürmez. Bağlama altyapısı daha sonra `FastDP` özelliğine bağlantılı olan bir sonraki <xref:System.Windows.Data.Binding> öğesi üzerine gider. Bu <xref:System.Windows.Data.Binding> "hızlı değer" değerini döndürür. <xref:System.Windows.Controls.TextBlock> artık "Fast Value" değerini görüntülüyor.  
  
 3 saniye geçtikten sonra, `SlowerDP` özelliği "daha yavaş değer" değerini döndürür. <xref:System.Windows.Controls.TextBlock> daha sonra "daha yavaş değer" değerini görüntüler.  
  
 5 saniye geçtikten sonra, `SlowestDP` özelliği "en yavaş değer" değerini döndürür. İlk olarak listelenen bu bağlama en yüksek önceliğe sahiptir. <xref:System.Windows.Controls.TextBlock> artık "en yavaş değer" değerini görüntülüyor.  
  
 Bir bağlamadan başarılı bir dönüş değeri olarak kabul edilen özellikler hakkında bilgi için bkz. <xref:System.Windows.Data.PriorityBinding>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
