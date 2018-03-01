---
title: "Nasıl yapılır: PriorityBinding Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e6ab8826f2298a8660a85d739fbe3456374b476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-prioritybinding"></a>Nasıl yapılır: PriorityBinding Uygulama
<xref:System.Windows.Data.PriorityBinding>içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağlamaların listesini belirterek çalışır. Bağlama Listesi en yüksek öncelikli olandan en düşük önceliği sıralanır. Yüksek önceliği olan bağlama bir değer döndürürse başarıyla işlendiğinde yoktur hiçbir zaman listedeki diğer bağlamaları işlem gerekmez. En yüksek öncelik bağlama değerlendirilmesi uzun süren durum olabilir, bir daha yüksek bir öncelik değeri başarıyla döndürünceye kadar başarılı bir şekilde bir değer döndüren bir sonraki en yüksek öncelikli kullanılır.  
  
## <a name="example"></a>Örnek  
 Göstermek için nasıl <xref:System.Windows.Data.PriorityBinding> çalışır, `AsyncDataSource` nesnesi şu üç özellik ile oluşturuldu: `FastDP`, `SlowerDP`, ve `SlowestDP`.  
  
 Get erişimcisine `FastDP` değerini döndürür `_fastDP` veri üyesi.  
  
 Get erişimcisine `SlowerDP` değerini dönmeden önce 3 saniye bekler `_slowerDP` veri üyesi.  
  
 Get erişimcisine `SlowestDP` değerini dönmeden önce 5 saniye bekler `_slowestDP` veri üyesi.  
  
> [!NOTE]
>  Bu örnek, yalnızca tanıtım amacıyla kullanılır. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Yönergeleri büyüklük alan kümesinden daha yavaş olan özellikleri tanımlamaya karşı önerilir. Daha fazla bilgi için bkz: [NIB: seçme arasında özellikleri ve yöntemleri](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Özelliğini bağlar yukarıdaki `AsyncDS` kullanarak <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Bağlama altyapısı işlediğinde <xref:System.Windows.Data.Binding> nesneleri, ilk başlar <xref:System.Windows.Data.Binding>, bağlı `SlowestDP` özelliği. Zaman bu <xref:System.Windows.Data.Binding> olduğundan, 5 saniye kadar sonraki uyku için işlenen, bir değer başarıyla dönmez <xref:System.Windows.Data.Binding> öğesi işlenir. Sonraki <xref:System.Windows.Data.Binding> 3 saniye için uyuyor için bir değer başarıyla döndürmüyor. Bağlama altyapısı ardından sonraki taşır <xref:System.Windows.Data.Binding> bağlı öğesi `FastDP` özelliği. Bu <xref:System.Windows.Data.Binding> "Fast Value" değeri döndürür. <xref:System.Windows.Controls.TextBlock> Şimdi value "Hızlı" görüntüler.  
  
 3 saniye geçtikten sonra `SlowerDP` özelliği "Yavaş Value" değeri döndürür. <xref:System.Windows.Controls.TextBlock> "Yavaş value" görüntüler.  
  
 5 saniye geçtikten sonra `SlowestDP` özelliği "Yavaş Value" değeri döndürür. İlk listelenmediğinden Bu bağlama en yüksek önceliğe sahiptir. <xref:System.Windows.Controls.TextBlock> Şimdi "yavaş value" değerini görüntüler.  
  
 Bkz: <xref:System.Windows.Data.PriorityBinding> bağlama gelen başarılı bir dönüş değeri olarak kabul hakkında bilgi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
