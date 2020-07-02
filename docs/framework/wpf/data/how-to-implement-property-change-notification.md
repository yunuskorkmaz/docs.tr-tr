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
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="70afe-103">Nasıl yapılır: Özellik Değişikliği Bildirimi Uygulama</span><span class="sxs-lookup"><span data-stu-id="70afe-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="70afe-104">Bağlama <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> hedefi özelliklerinizi bağlama kaynağının dinamik değişikliklerini otomatik olarak yansıtacak şekilde etkinleştirmek için (örneğin, Kullanıcı bir formu düzenlediğinde Önizleme bölmesinin otomatik olarak güncelleştirilmesini sağlamak için), sınıfınızın doğru özellik değişmiş bildirimleri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="70afe-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="70afe-105">Bu örnek, uygulayan bir sınıfın nasıl oluşturulacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="70afe-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70afe-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="70afe-106">Example</span></span>  
 <span data-ttu-id="70afe-107">Uygulamak için, <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayı bildirmeniz ve metodunu oluşturmanız gerekir `OnPropertyChanged` .</span><span class="sxs-lookup"><span data-stu-id="70afe-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="70afe-108">Ardından, değişiklik bildirimlerini istediğiniz her özellik için, `OnPropertyChanged` özelliği her güncelleştirildiğinde çağırın.</span><span class="sxs-lookup"><span data-stu-id="70afe-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="70afe-109">Sınıfın bağlamayı desteklemek için nasıl kullanılabileceği hakkında bir örnek görmek için `Person` <xref:System.Windows.Data.BindingMode.TwoWay> , bkz. [TextBox metni kaynağı güncelleştirdikleri zaman denetim](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="70afe-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70afe-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70afe-110">See also</span></span>

- [<span data-ttu-id="70afe-111">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="70afe-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="70afe-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="70afe-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="70afe-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="70afe-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
