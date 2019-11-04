---
title: 'Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454953"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama
Bu örnek, bağlama hedefi (hedef) veya bir bağlamanın bağlama kaynağı (kaynak) özelliği güncelleştirildikten sonra bildirim yapılacak şekilde nasıl ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bağlama kaynağı veya hedefi her güncelleştirildiği zaman bir veri güncelleştirme olayı başlatır. Bu olay, bağlantılı veriler değiştiğinden, güncelleştirilmesi gereken [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bilgilendirmek için kullanılır. Bu olayların çalışması ve aynı zamanda tek yönlü veya iki yönlü bağlamanın düzgün şekilde çalışması için, <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini kullanarak veri sınıfınızı uygulamanız gerektiğini unutmayın. Daha fazla bilgi için bkz. [özellik değişiklik bildirimini uygulama](how-to-implement-property-change-notification.md).  
  
 <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> veya <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> özelliğini (ya da her ikisi) bağlamadaki `true` ayarlayın. Bu olayı dinlemek için sağladığınız işleyicinin, değişiklikler hakkında bilgi almak istediğiniz öğeye doğrudan iliştirilmeli veya bağlamdaki herhangi bir şeyin değiştiği farkında olmak istiyorsanız genel veri bağlamına eklenmelidir.  
  
 Bir hedef özellik güncelleştirildiği zaman bildirim için ayarlamayı gösteren bir örnek aşağıda verilmiştir.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Daha sonra, olayı işlemek için bu örnekteki *OnTargetUpdated*\<t > temsilcisine göre bir işleyici atayabilirsiniz:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Olayın parametreleri, tek bir öğede birden fazla bağlı özellik olması halinde, değiştirilen Özellik (örneğin, tür veya aynı işleyici birden fazla öğeye eklenmişse) hakkındaki ayrıntıları belirlemede kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
