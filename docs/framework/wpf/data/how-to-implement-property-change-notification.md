---
title: "Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6674628acd4ea6b18f98a0ab5e20935220595de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="af21d-102">Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama</span><span class="sxs-lookup"><span data-stu-id="af21d-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="af21d-103">Desteklemek için <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> otomatik olarak (örneğin kullanıcı formu düzenlediğinde otomatik olarak güncelleştirilen Önizleme bölmesine sahip olmak için), bağlama kaynağının dinamik değişiklikleri yansıtacak şekilde, bağlama hedef özellikleri etkinleştirmek için bağlama, sınıf uygun özellik değişikliği bildirimlerini sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af21d-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="af21d-104">Bu örnek uygulayan bir sınıf oluşturmak nasıl gösterir <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="af21d-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af21d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="af21d-105">Example</span></span>  
 <span data-ttu-id="af21d-106">Uygulanacak <xref:System.ComponentModel.INotifyPropertyChanged> bildirmeniz gerekir <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay ve oluşturma `OnPropertyChanged` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af21d-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="af21d-107">Değişiklik bildirimleri arayın, istediğiniz her bir özellik için sonra `OnPropertyChanged` özelliği her güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="af21d-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="af21d-108">Bir örneğini nasıl görmek için `Person` sınıfı desteklemek için kullanılabilir <xref:System.Windows.Data.BindingMode.TwoWay> bağlama, bkz: [zaman TextBox metni kaynak güncelleştirmelerini denetlemek](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="af21d-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af21d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af21d-109">See Also</span></span>  
 [<span data-ttu-id="af21d-110">Bağlama kaynaklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="af21d-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="af21d-111">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="af21d-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="af21d-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="af21d-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
