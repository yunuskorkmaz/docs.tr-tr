---
title: 'Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama'
description: Windows Presentation Foundation (WPF) ' de özellik değeri değiştiğinde bağlama kaynağını otomatik olarak bildirmek için özelliklerinizi etkinleştirin.
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620787"
---
# <a name="how-to-implement-property-change-notification"></a>Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama
Bağlama <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> hedefi özelliklerinizi bağlama kaynağının dinamik değişikliklerini otomatik olarak yansıtacak şekilde etkinleştirmek için (örneğin, Kullanıcı bir formu düzenlediğinde Önizleme bölmesinin otomatik olarak güncelleştirilmesini sağlamak için), sınıfınızın doğru özellik değişmiş bildirimleri sağlaması gerekir. Bu örnek, uygulayan bir sınıfın nasıl oluşturulacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> .  
  
## <a name="example"></a>Örnek  
 Uygulamak için, <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayı bildirmeniz ve metodunu oluşturmanız gerekir `OnPropertyChanged` . Ardından, değişiklik bildirimlerini istediğiniz her özellik için, `OnPropertyChanged` özelliği her güncelleştirildiğinde çağırın.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Sınıfın bağlamayı desteklemek için nasıl kullanılabileceği hakkında bir örnek görmek için `Person` <xref:System.Windows.Data.BindingMode.TwoWay> , bkz. [TextBox metni kaynağı güncelleştirdikleri zaman denetim](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
