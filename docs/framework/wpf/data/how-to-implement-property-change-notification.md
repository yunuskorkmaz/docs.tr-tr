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
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="3a2b6-102">Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama</span><span class="sxs-lookup"><span data-stu-id="3a2b6-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="3a2b6-103">Bağlama hedefi özelliklerinin, bağlama kaynağının dinamik değişikliklerini otomatik olarak yansıtmasını sağlamak üzere <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı desteklemek için (örneğin, Kullanıcı bir formu düzenlediğinde Önizleme bölmesinin otomatik olarak güncelleştirilmesini sağlamak için), sınıfınızın şunu yapması gerekir uygun özellik değişmiş bildirimleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="3a2b6-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="3a2b6-104">Bu örnek, <xref:System.ComponentModel.INotifyPropertyChanged>uygulayan bir sınıfın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a2b6-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a2b6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a2b6-105">Example</span></span>  
 <span data-ttu-id="3a2b6-106"><xref:System.ComponentModel.INotifyPropertyChanged> uygulamak için <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayını bildirmeniz ve `OnPropertyChanged` metodunu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a2b6-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="3a2b6-107">Ardından, değişiklik bildirimlerini istediğiniz her bir özellik için, özellik güncelleştirildiğinde `OnPropertyChanged` çağırın.</span><span class="sxs-lookup"><span data-stu-id="3a2b6-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="3a2b6-108">`Person` sınıfının <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı desteklemek için nasıl kullanılabileceği hakkında bir örnek görmek için, bkz. [TextBox metni kaynağı güncelleştirdikleri zaman denetim](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="3a2b6-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a2b6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a2b6-109">See also</span></span>

- [<span data-ttu-id="3a2b6-110">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3a2b6-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="3a2b6-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3a2b6-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3a2b6-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3a2b6-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
