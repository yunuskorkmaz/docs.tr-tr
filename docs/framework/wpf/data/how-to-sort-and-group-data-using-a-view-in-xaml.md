---
title: 'Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460118"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="7ce67-102">Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="7ce67-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="7ce67-103">Bu örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]' de bir veri koleksiyonunun bir görünümünün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ce67-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="7ce67-104">Görünümler gruplandırma, sıralama, filtreleme ve geçerli bir öğenin kavramının işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ce67-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce67-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ce67-105">Example</span></span>  
 <span data-ttu-id="7ce67-106">Aşağıdaki örnekte, *yerleri* adlı statik kaynak, her bir *Yerleştir* nesnesinin bir şehir adı ve eyalet olarak oluşturulduğu bir *Yerleştir* nesneleri koleksiyonu olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ce67-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="7ce67-107">*Src* ön eki, veri kaynağı *yerlerinin* tanımlandığı ad alanı ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7ce67-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="7ce67-108">*SCM* ön eki, `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"``"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ve *dat* eşlemeleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7ce67-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="7ce67-109">Aşağıdaki örnek, şehir adına göre sıralanmış ve duruma göre gruplandırılan veri koleksiyonunun bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ce67-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="7ce67-110">Görünüm daha sonra aşağıdaki örnekte olduğu gibi bir bağlama kaynağı olabilir:</span><span class="sxs-lookup"><span data-stu-id="7ce67-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="7ce67-111">Bir <xref:System.Windows.Data.XmlDataProvider> kaynağında tanımlanan XML verilerine bağlamalar için, XML adından önce bir @ simgesiyle önüne geçin.</span><span class="sxs-lookup"><span data-stu-id="7ce67-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="7ce67-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ce67-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="7ce67-113">Veri Koleksiyonunun Varsayılan Görünümünü Alma</span><span class="sxs-lookup"><span data-stu-id="7ce67-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="7ce67-114">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ce67-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7ce67-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7ce67-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
