---
title: 'Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051994"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama
Bu örnek, bağlama hedefi (hedef) veya bir bağlamanın bağlama (kaynak) kaynak özelliği güncelleştirildiğinde bildirim almak için nasıl ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Veri güncelleştirme her zaman bağlama kaynağı veya hedefi güncelleştirildiğini olayını oluşturur. Bu olay bildirmek için dahili olarak kullanılan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bağlı veriler değiştiğinden, bu, güncelleştirmeniz gerekir. Bu olaylar için ve ayrıca düzgün çalışması için tek yönlü veya çift yönlü bağlama için sınıfı kullanarak verilerinizi uygulamak gerektiğini unutmayın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md).  
  
 Ayarlama <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> veya <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> özelliği (veya her ikisi de) `true` bağlamasında. Bağlam içinde herhangi bir şey değişti bilincinde olmasını istiyorsanız bu olay için dinleme sağladığınız işleyici değişikliklerin bildirilmesini istediğiniz öğeye doğrudan ya da genel veri bağlamı bağlanması gerekir.  
  
 Bir hedef özelliği güncelleştirildiğinde bildirim için ayarlanmış gösteren bir örnek aşağıda verilmiştir.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Ardından EventHandler üzerinde bağlı bir işleyici atayabilirsiniz\<T > temsilcisi, *EventHandler* olayı işlemek için bu örnekte:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Olay parametrelerinin (türü veya aynı işleyici için birden fazla öğe eklediyseniz öğe gibi), değiştirilen özelliğin ayrıntılarını belirlemek için kullanılabilir olan tek bir öğede birden çok ilişkili özellikler varsa yararlı olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
