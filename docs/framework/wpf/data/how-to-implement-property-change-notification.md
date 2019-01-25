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
ms.openlocfilehash: 7a8ab232019f1266095091cd4e1ce6e7fec63207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587820"
---
# <a name="how-to-implement-property-change-notification"></a>Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama
Desteklemek için <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> otomatik olarak bağlama kaynağının (örneğin kullanıcı, bir form düzenlediğinde otomatik olarak güncelleştirilen Önizleme bölmesinde sağlamak için), dinamik değişiklikleri yansıtacak şekilde, bağlama hedefi özellikleri etkinleştirmek için bağlama, sınıfı uygun özellik değişikliği bildirimleri sağlaması gerekir. Bu örnekte, uygulayan bir sınıf oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Örnek  
 Uygulamak için <xref:System.ComponentModel.INotifyPropertyChanged> bildirmenize gerek <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay oluşturup `OnPropertyChanged` yöntemi. Her bir özellik için değişiklik bildirimleri arayın, istediğiniz sonra `OnPropertyChanged` özelliği her güncelleştirildiğinde.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Nasıl bir örnek için `Person` sınıfı desteklemek için kullanılabilir <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı bkz [TextBox metni kaynağı, güncelleştirmeleri denetlemek](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
