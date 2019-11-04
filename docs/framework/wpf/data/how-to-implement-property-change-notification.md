---
title: 'Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459752"
---
# <a name="how-to-implement-property-change-notification"></a>Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama
Bağlama hedefi özelliklerinin, bağlama kaynağının dinamik değişikliklerini otomatik olarak yansıtmasını sağlamak üzere <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı desteklemek için (örneğin, Kullanıcı bir formu düzenlediğinde Önizleme bölmesinin otomatik olarak güncelleştirilmesini sağlamak için), sınıfınızın şunu yapması gerekir uygun özellik değişmiş bildirimleri sağlayın. Bu örnek, <xref:System.ComponentModel.INotifyPropertyChanged>uygulayan bir sınıfın nasıl oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.ComponentModel.INotifyPropertyChanged> uygulamak için <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayını bildirmeniz ve `OnPropertyChanged` metodunu oluşturmanız gerekir. Ardından, değişiklik bildirimlerini istediğiniz her bir özellik için, özellik güncelleştirildiğinde `OnPropertyChanged` çağırın.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 `Person` sınıfının <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı desteklemek için nasıl kullanılabileceği hakkında bir örnek görmek için, bkz. [TextBox metni kaynağı güncelleştirdikleri zaman denetim](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
