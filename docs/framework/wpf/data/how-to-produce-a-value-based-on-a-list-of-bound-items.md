---
title: 'Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459698"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="c1707-102">Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme</span><span class="sxs-lookup"><span data-stu-id="c1707-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="c1707-103"><xref:System.Windows.Data.MultiBinding>, bir bağlama hedefi özelliğini kaynak Özellikler listesine bağlamanıza olanak tanır ve ardından belirtilen girdilerle bir değer üretmek için mantık uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="c1707-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="c1707-104">Bu örnek <xref:System.Windows.Data.MultiBinding>nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1707-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1707-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1707-105">Example</span></span>  
 <span data-ttu-id="c1707-106">Aşağıdaki örnekte `NameListData`, `firstName` ve `lastName`iki özellik içeren nesneler olan `PersonName` nesneleri koleksiyonunu ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c1707-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="c1707-107">Aşağıdaki örnek, ilk adı en başta olan bir kişinin ilk ve son adlarını gösteren bir <xref:System.Windows.Controls.TextBlock> üretir.</span><span class="sxs-lookup"><span data-stu-id="c1707-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="c1707-108">Son ad-ilk biçiminin nasıl üretildiğini anlamak için `NameConverter`uygulamasına göz atalım:</span><span class="sxs-lookup"><span data-stu-id="c1707-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="c1707-109">`NameConverter` <xref:System.Windows.Data.IMultiValueConverter> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="c1707-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="c1707-110">`NameConverter`, bireysel bağlamalardan değerleri alır ve değerler nesne dizisinde depolar.</span><span class="sxs-lookup"><span data-stu-id="c1707-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="c1707-111"><xref:System.Windows.Data.Binding> öğelerinin <xref:System.Windows.Data.MultiBinding> öğesi altında göründüğü sıra, bu değerlerin dizide depolanma sıradır.</span><span class="sxs-lookup"><span data-stu-id="c1707-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="c1707-112"><xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliğin değeri, <xref:System.Windows.Data.MultiBinding.Converter%2A> yönteminin parametre bağımsız değişkeni tarafından başvurulur, bu da adın nasıl biçimlendirileceğini belirleyen parametreyi bir anahtar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c1707-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1707-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1707-113">See also</span></span>

- [<span data-ttu-id="c1707-114">Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c1707-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="c1707-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1707-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c1707-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c1707-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
