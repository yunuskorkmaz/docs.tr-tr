---
title: "Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c219def87e258a2c9fc1bf4f4867287e6156c59a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="dbefa-102">Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="dbefa-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="dbefa-103">Bu örnek, bir veri toplama bir görünümün nasıl oluşturulacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbefa-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="dbefa-104">Görünümler gruplandırma, sıralama, filtreleme işlevler ve güncel bir öğenin kavramı izin verir.</span><span class="sxs-lookup"><span data-stu-id="dbefa-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbefa-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbefa-105">Example</span></span>  
 <span data-ttu-id="dbefa-106">Aşağıdaki örnekte, statik kaynak adlı *yerleştirir* koleksiyonu olarak tanımlanır *yer* her nesneleri *yer* nesne şehir adını içermektedir ve durumu.</span><span class="sxs-lookup"><span data-stu-id="dbefa-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="dbefa-107">Önek *src* ad alanına eşlenen burada veri kaynağı *yerler* tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dbefa-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="dbefa-108">Önek *scm* eşlendiği `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ve *verilerinin* eşlendiği `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="dbefa-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="dbefa-109">Aşağıdaki örnek Şehir adına göre sıralanır ve duruma göre gruplandırılmış veri koleksiyonunun bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbefa-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="dbefa-110">Görünüm sonra aşağıdaki örnekteki gibi bir bağlama kaynağı olabilir:</span><span class="sxs-lookup"><span data-stu-id="dbefa-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="dbefa-111">Bağlamaları tanımlanan XML veri için bir <xref:System.Windows.Data.XmlDataProvider> kaynak XML adından bir @ simgesinden.</span><span class="sxs-lookup"><span data-stu-id="dbefa-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="dbefa-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbefa-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="dbefa-113">Veri toplama varsayılan görünümünü Al</span><span class="sxs-lookup"><span data-stu-id="dbefa-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="dbefa-114">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="dbefa-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="dbefa-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="dbefa-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
