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
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="dd2b0-102">Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama</span><span class="sxs-lookup"><span data-stu-id="dd2b0-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="dd2b0-103">Desteklemek için <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> otomatik olarak bağlama kaynağının (örneğin kullanıcı, bir form düzenlediğinde otomatik olarak güncelleştirilen Önizleme bölmesinde sağlamak için), dinamik değişiklikleri yansıtacak şekilde, bağlama hedefi özellikleri etkinleştirmek için bağlama, sınıfı uygun özellik değişikliği bildirimleri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd2b0-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="dd2b0-104">Bu örnekte, uygulayan bir sınıf oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="dd2b0-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd2b0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd2b0-105">Example</span></span>  
 <span data-ttu-id="dd2b0-106">Uygulamak için <xref:System.ComponentModel.INotifyPropertyChanged> bildirmenize gerek <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay oluşturup `OnPropertyChanged` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd2b0-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="dd2b0-107">Her bir özellik için değişiklik bildirimleri arayın, istediğiniz sonra `OnPropertyChanged` özelliği her güncelleştirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="dd2b0-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="dd2b0-108">Nasıl bir örnek için `Person` sınıfı desteklemek için kullanılabilir <xref:System.Windows.Data.BindingMode.TwoWay> bağlamayı bkz [TextBox metni kaynağı, güncelleştirmeleri denetlemek](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="dd2b0-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2b0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd2b0-109">See also</span></span>
- [<span data-ttu-id="dd2b0-110">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd2b0-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [<span data-ttu-id="dd2b0-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd2b0-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="dd2b0-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="dd2b0-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
