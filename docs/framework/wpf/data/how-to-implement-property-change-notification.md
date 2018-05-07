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
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-property-change-notification"></a>Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama
Desteklemek için <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> otomatik olarak (örneğin kullanıcı formu düzenlediğinde otomatik olarak güncelleştirilen Önizleme bölmesine sahip olmak için), bağlama kaynağının dinamik değişiklikleri yansıtacak şekilde, bağlama hedef özellikleri etkinleştirmek için bağlama, sınıf uygun özellik değişikliği bildirimlerini sağlaması gerekir. Bu örnek uygulayan bir sınıf oluşturmak nasıl gösterir <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Örnek  
 Uygulanacak <xref:System.ComponentModel.INotifyPropertyChanged> bildirmeniz gerekir <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay ve oluşturma `OnPropertyChanged` yöntemi. Değişiklik bildirimleri arayın, istediğiniz her bir özellik için sonra `OnPropertyChanged` özelliği her güncelleştirilir.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Bir örneğini nasıl görmek için `Person` sınıfı desteklemek için kullanılabilir <xref:System.Windows.Data.BindingMode.TwoWay> bağlama, bkz: [zaman TextBox metni kaynak güncelleştirmelerini denetlemek](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
