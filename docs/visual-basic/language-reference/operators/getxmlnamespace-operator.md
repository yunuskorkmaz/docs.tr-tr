---
title: GetXmlNamespace İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353185"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="b427a-102">GetXmlNamespace İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b427a-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="b427a-103">Belirtilen XML ad alanı ön ekine karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="b427a-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b427a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b427a-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="b427a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b427a-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="b427a-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b427a-106">Optional.</span></span> <span data-ttu-id="b427a-107">XML ad alanı önekini tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="b427a-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="b427a-108">Sağlanırsa, bu dize geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b427a-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="b427a-109">Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b427a-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="b427a-110">Hiçbir önek belirtilmemişse, varsayılan ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b427a-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="b427a-111">Varsayılan ad alanı belirtilmemişse boş ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b427a-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b427a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b427a-112">Return Value</span></span>  
 <span data-ttu-id="b427a-113">XML ad alanı ön ekine karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b427a-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b427a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b427a-114">Remarks</span></span>  
 <span data-ttu-id="b427a-115">`GetXmlNamespace` işleci, XML ad alanı öneki `xmlNamespacePrefix`karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="b427a-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="b427a-116">XML ad alanı öneklerini doğrudan XML değişmez değerleri ve XML eksen özellikleri içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b427a-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="b427a-117">Ancak, kodunuzda kullanabilmeniz için bir ad alanı önekini bir <xref:System.Xml.Linq.XNamespace> nesnesine dönüştürmek üzere `GetXmlNamespace` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b427a-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="b427a-118">Birçok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yönteminin gerektirdiği tam bir <xref:System.Xml.Linq.XName> nesnesini almak için bir <xref:System.Xml.Linq.XNamespace> nesnesine nitelenmemiş bir öğe adı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b427a-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b427a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b427a-119">Example</span></span>  
 <span data-ttu-id="b427a-120">Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="b427a-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b427a-121">Daha sonra, bir XML sabit değeri oluşturmak ve nitelenmiş ada sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="b427a-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="b427a-122">Daha sonra bu alt düğümü, `GetXmlNamespace` işlecini kullanarak tam adı oluşturan `ShowName` alt yordama geçirir.</span><span class="sxs-lookup"><span data-stu-id="b427a-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="b427a-123">`ShowName` alt yordamı daha sonra üst `ns:contact` düğümünü almak için tam adı <xref:System.Xml.Linq.XNode.Ancestors%2A> yöntemine geçirir.</span><span class="sxs-lookup"><span data-stu-id="b427a-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="b427a-124">`TestGetXmlNamespace.RunSample()`çağırdığınızda, aşağıdaki metni içeren bir ileti kutusu görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="b427a-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b427a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b427a-125">See also</span></span>

- [<span data-ttu-id="b427a-126">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="b427a-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="b427a-127">Visual Basic XML 'e erişme</span><span class="sxs-lookup"><span data-stu-id="b427a-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
