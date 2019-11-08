---
title: 'Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740581"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="618cd-102">Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="618cd-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="618cd-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="618cd-103">Example</span></span>
 <span data-ttu-id="618cd-104">Bu örnek, XML bağlama kaynağınızda belirtilen ad alanlarının nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="618cd-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="618cd-105">XML verilerinizde aşağıdaki XML ad alanı tanımı varsa:</span><span class="sxs-lookup"><span data-stu-id="618cd-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="618cd-106">Aşağıdaki örnekte olduğu gibi, ad alanını bir <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>eşlemek için <xref:System.Windows.Data.XmlNamespaceMapping> öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="618cd-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="618cd-107">Ardından, XML ad alanına başvurmak için <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="618cd-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="618cd-108">Bu örnekteki <xref:System.Windows.Controls.ListBox> *başlık* ve *DC:* her *öğenin*tarihini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="618cd-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="618cd-109">Belirttiğiniz <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> XML kaynağında kullanılan ile eşleşmesi gerekmez; ön ek XML kaynağındaki önek değişirse eşlemenin hala işe yarar.</span><span class="sxs-lookup"><span data-stu-id="618cd-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="618cd-110">Bu örnekte, XML verileri bir Web hizmetinden gelir, ancak <xref:System.Windows.Data.XmlNamespaceMapping> öğesi, gömülü bir dosyadaki satır içi XML veya XML verileriyle de birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="618cd-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="618cd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618cd-111">See also</span></span>

- [<span data-ttu-id="618cd-112">XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="618cd-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="618cd-113">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="618cd-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="618cd-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="618cd-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
