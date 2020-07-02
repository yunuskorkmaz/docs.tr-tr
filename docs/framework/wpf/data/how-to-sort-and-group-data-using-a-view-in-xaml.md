---
title: 'Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma'
description: Windows Presentation Foundation (WPF) içinde gruplandırma, sıralama ve filtreleme için bir veri koleksiyonunun görünümünü oluşturmayı öğrenin.
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
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621684"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="01cf1-103">Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="01cf1-103">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="01cf1-104">Bu örnek, ' de bir veri koleksiyonunun bir görünümünün nasıl oluşturulacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="01cf1-104">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="01cf1-105">Görünümler gruplandırma, sıralama, filtreleme ve geçerli bir öğenin kavramının işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="01cf1-105">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01cf1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="01cf1-106">Example</span></span>  
 <span data-ttu-id="01cf1-107">Aşağıdaki örnekte, *yerleri* adlı statik kaynak, her bir *Yerleştir* nesnesinin bir şehir adı ve eyalet olarak oluşturulduğu bir *Yerleştir* nesneleri koleksiyonu olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01cf1-107">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="01cf1-108">*Src* ön eki, veri kaynağı *yerlerinin* tanımlandığı ad alanı ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01cf1-108">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="01cf1-109">*SCM* öneki `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ile ve *dat* Maps ile eşlenir `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .</span><span class="sxs-lookup"><span data-stu-id="01cf1-109">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="01cf1-110">Aşağıdaki örnek, şehir adına göre sıralanmış ve duruma göre gruplandırılan veri koleksiyonunun bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01cf1-110">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="01cf1-111">Görünüm daha sonra aşağıdaki örnekte olduğu gibi bir bağlama kaynağı olabilir:</span><span class="sxs-lookup"><span data-stu-id="01cf1-111">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="01cf1-112">Bir kaynakta tanımlanan XML verilerine bağlamalar için <xref:System.Windows.Data.XmlDataProvider> , XML adından önce bir @ simgesiyle önüne geçin.</span><span class="sxs-lookup"><span data-stu-id="01cf1-112">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="01cf1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01cf1-113">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="01cf1-114">Veri koleksiyonunun varsayılan görünümünü al</span><span class="sxs-lookup"><span data-stu-id="01cf1-114">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="01cf1-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01cf1-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="01cf1-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="01cf1-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
