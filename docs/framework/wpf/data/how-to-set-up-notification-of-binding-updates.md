---
title: "Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a07337e99e985bfbc0a5dbc5f2d231ee36cf1422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama
Bu örnek, bağlama hedefinin (hedef) veya bir bağlama bağlama source (kaynak) özelliğini güncelleştirildiğinde bildirim almak için nasıl ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Veri güncelleştirme her zaman bağlama kaynak veya hedef güncelleştirildi olayını oluşturur. Bu olay bildirmek için dahili olarak kullanılan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ilişkili veri değiştiğinden, bu, güncelleştirmeniz gerekir. Bu olayların çalışmak ve ayrıca düzgün çalışması için tek veya çift yönlü bağlama, sınıf kullanarak verilerinizi uygulamak gerektiğini unutmayın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Ayarlama <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> veya <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> özelliği (veya her ikisi de) `true` bağlamada. Bağlamda herhangi bir şey değiştiğini unutmayın istiyorsanız, bu olay için dinleme sağlamak işleyicisine doğrudan değişikliklerden haberdar olmak istediğiniz öğe veya genel veri bağlamı bağlı olması gerekir.  
  
 Burada, bildirim için bir hedef özellik güncelleştirildiği ayarlamak nasıl oluşturulduğunu gösteren bir örnek verilmiştir.  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Ardından OnTargetUpdated, bağlı bir işleyici atayabilirsiniz\<T > temsilci, *EventHandler* olayını işlemek için bu örnekte:  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Olay parametrelerinin (türü ya da aynı işleyici birden fazla öğeye bağlı olduğu belirli öğe gibi) değiştirilmiş özellik ayrıntılarını belirlemek için kullanılabilir olan tek bir öğede birden çok ilişkili özellikleri varsa yararlı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
