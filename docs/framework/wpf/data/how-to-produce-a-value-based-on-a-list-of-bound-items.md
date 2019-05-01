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
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931416"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="20191-102">Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme</span><span class="sxs-lookup"><span data-stu-id="20191-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="20191-103"><xref:System.Windows.Data.MultiBinding> bir bağlama hedefi özelliği kaynak özellikleri listesine bağlayın ve sonra verilen girişleri bir değerle bağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20191-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="20191-104">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="20191-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20191-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="20191-105">Example</span></span>  
 <span data-ttu-id="20191-106">Aşağıdaki örnekte, `NameListData` bir koleksiyonuna başvuruyor `PersonName` iki özellikleri içeren nesneleri olan nesneleri `firstName` ve `lastName`.</span><span class="sxs-lookup"><span data-stu-id="20191-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="20191-107">Aşağıdaki örnek üreten bir <xref:System.Windows.Controls.TextBlock> ilk ve son adlarıyla bir kişinin soyadı ilk gösterir.</span><span class="sxs-lookup"><span data-stu-id="20191-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="20191-108">Son adı ilk biçiminin nasıl üretildiğini anlamak için bir uygulaması bakalım `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="20191-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="20191-109">`NameConverter` uygulayan <xref:System.Windows.Data.IMultiValueConverter> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="20191-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="20191-110">`NameConverter` değerleri tek tek bağlamaları alır ve değerleri nesne dizide saklar.</span><span class="sxs-lookup"><span data-stu-id="20191-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="20191-111">Bir sırayı <xref:System.Windows.Data.Binding> öğeleri görünür altında <xref:System.Windows.Data.MultiBinding> öğedir sırası dizideki değerleri depolanır.</span><span class="sxs-lookup"><span data-stu-id="20191-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="20191-112">Değerini <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliği parametre bağımsız değişkeni tarafından başvurulan <xref:System.Windows.Data.MultiBinding.Converter%2A> parametrenin adını biçimlendirmek nasıl belirlemek için bir anahtar gerçekleştiren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20191-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20191-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20191-113">See also</span></span>

- [<span data-ttu-id="20191-114">Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="20191-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="20191-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="20191-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="20191-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="20191-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
