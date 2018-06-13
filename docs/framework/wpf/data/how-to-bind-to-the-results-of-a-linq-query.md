---
title: 'Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d374bb69b6b7e022497403b9591b27e9ad7e2395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554999"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="86465-102">Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama</span><span class="sxs-lookup"><span data-stu-id="86465-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="86465-103">Bu örnek, bir LINQ Sorgu çalıştırmak ve sonuçları bağlamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="86465-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86465-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="86465-104">Example</span></span>  
 <span data-ttu-id="86465-105">Aşağıdaki örnek, iki liste kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86465-105">The following example creates two list boxes.</span></span> <span data-ttu-id="86465-106">İlk liste kutusu üç liste öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="86465-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="86465-107">Bir öğenin ilk liste kutusundan seçilmesi, aşağıdaki olay işleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="86465-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="86465-108">Bu örnekte, `Tasks` koleksiyonudur `Task` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="86465-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="86465-109">`Task` Sınıfı adlı bir özelliğe sahiptir `Priority`.</span><span class="sxs-lookup"><span data-stu-id="86465-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="86465-110">Bu olay işleyicisi koleksiyonu döndüren LINQ sorgusu çalıştırır `Task` , seçili öncelik değerine sahip ve aynı ayarlar nesneleri <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="86465-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="86465-111">İkinci liste kutusunu o koleksiyona bağlar çünkü kendi <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> değeri ayarı `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="86465-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="86465-112">Sonuç olarak döndürülen koleksiyon gösterilir (temel `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="86465-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86465-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86465-113">See Also</span></span>  
 [<span data-ttu-id="86465-114">XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="86465-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="86465-115">Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="86465-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="86465-116">WPF Sürüm 4.5'teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="86465-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="86465-117">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86465-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="86465-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="86465-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
