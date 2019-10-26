---
title: 'Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919662"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="68bf1-102">Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="68bf1-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="68bf1-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="68bf1-103">Example</span></span>
 <span data-ttu-id="68bf1-104">Bu örnek, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] bağlama kaynağınızda belirtilen ad alanlarının nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68bf1-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>

 <span data-ttu-id="68bf1-105">[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileriniz aşağıdaki [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı tanımına sahipse:</span><span class="sxs-lookup"><span data-stu-id="68bf1-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="68bf1-106">Aşağıdaki örnekte olduğu gibi, ad alanını bir <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>eşlemek için <xref:System.Windows.Data.XmlNamespaceMapping> öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68bf1-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="68bf1-107">Daha sonra, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanına başvurmak için <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68bf1-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="68bf1-108">Bu örnekteki <xref:System.Windows.Controls.ListBox> *başlık* ve *DC:* her *öğenin*tarihini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68bf1-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="68bf1-109">Belirttiğiniz <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynağında kullanılan ile eşleşmesi gerekmez; önek [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynak üzerinde değişirse eşlemenin hala işe yarar.</span><span class="sxs-lookup"><span data-stu-id="68bf1-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>

 <span data-ttu-id="68bf1-110">Bu örnekte, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri bir Web hizmetinden gelir, ancak <xref:System.Windows.Data.XmlNamespaceMapping> öğesi, gömülü bir dosyadaki satır içi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veya [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerle de birlikte da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="68bf1-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="68bf1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68bf1-111">See also</span></span>

- [<span data-ttu-id="68bf1-112">XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="68bf1-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="68bf1-113">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="68bf1-113">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="68bf1-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="68bf1-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
