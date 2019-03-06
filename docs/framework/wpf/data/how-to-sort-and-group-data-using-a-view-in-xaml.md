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
ms.openlocfilehash: 01cbd113502c3f953bd701930df6db090844fefa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351430"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="3b2bb-102">Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="3b2bb-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="3b2bb-103">Bu örnek, bir veri toplama bir görünümün nasıl oluşturulacağını gösterir. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b2bb-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="3b2bb-104">Görünümler işlevleri gruplandırma, sıralama, filtreleme ve geçerli öğenin kavram izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b2bb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b2bb-105">Example</span></span>  
 <span data-ttu-id="3b2bb-106">Aşağıdaki örnekte adlı statik kaynak *yerleştirir* koleksiyonu olarak tanımlanır *yerde* nesneleri, her *yerde* nesne bir şehir adı toplamda ve durumu.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="3b2bb-107">Önek *src* ad alanına eşlenen burada veri kaynağı *yerler* tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="3b2bb-108">Önek *scm* eşlendiği `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ve *dat* eşlendiği `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="3b2bb-109">Aşağıdaki örnek Şehir adına göre sıralanır ve durumlarına göre gruplandırılan veri koleksiyonunu bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="3b2bb-110">Görünüm, ardından aşağıdaki örnekteki gibi bir bağlama kaynağı olabilir:</span><span class="sxs-lookup"><span data-stu-id="3b2bb-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="3b2bb-111">Tanımlanan XML veri bağlama için bir <xref:System.Windows.Data.XmlDataProvider> kaynak ile XML adın önüne bir @ sembolü.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="3b2bb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b2bb-112">See also</span></span>
- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="3b2bb-113">Veri Koleksiyonunun Varsayılan Görünümünü Alma</span><span class="sxs-lookup"><span data-stu-id="3b2bb-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="3b2bb-114">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b2bb-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3b2bb-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3b2bb-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
