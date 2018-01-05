---
title: "Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme"
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
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="9a87b-102">Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme</span><span class="sxs-lookup"><span data-stu-id="9a87b-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="9a87b-103"><xref:System.Windows.Data.MultiBinding>Kaynak özelliklerinin bir listesi için bir bağlama hedef özelliği bağlamak ve sonra verilen girişleri bir değerle bağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a87b-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="9a87b-104">Bu örnek nasıl kullanılacağı ortaya <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="9a87b-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a87b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a87b-105">Example</span></span>  
 <span data-ttu-id="9a87b-106">Aşağıdaki örnekte, `NameListData` koleksiyonuna başvuruyor `PersonName` iki özellikleri içeren nesneleri olan nesneleri `firstName` ve `lastName`.</span><span class="sxs-lookup"><span data-stu-id="9a87b-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="9a87b-107">Aşağıdaki örnek üreten bir <xref:System.Windows.Controls.TextBlock> ilk ve son adlarıyla bir kişinin soyadını ilk gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a87b-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="9a87b-108">Son adı ilk biçimi nasıl üretilen anlamak için bir uygulaması bakalım `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="9a87b-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="9a87b-109">`NameConverter`uygulayan <xref:System.Windows.Data.IMultiValueConverter> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9a87b-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="9a87b-110">`NameConverter`ayrı bağlantılardan değerleri alır ve bunları değerleri nesne dizisinin içinde depolar.</span><span class="sxs-lookup"><span data-stu-id="9a87b-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="9a87b-111">Hangi sırayla <xref:System.Windows.Data.Binding> öğeleri görünür altında <xref:System.Windows.Data.MultiBinding> bu değerleri dizisinde depolanır sipariş bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="9a87b-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="9a87b-112">Değeri <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliği parametre bağımsız değişkeni tarafından başvurulan <xref:System.Windows.Data.MultiBinding.Converter%2A> parametrenin adı biçimlendirme belirlemek için bir anahtar gerçekleştirir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a87b-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a87b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a87b-113">See Also</span></span>  
 [<span data-ttu-id="9a87b-114">Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="9a87b-114">Convert Bound Data</span></span>](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [<span data-ttu-id="9a87b-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a87b-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9a87b-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9a87b-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
