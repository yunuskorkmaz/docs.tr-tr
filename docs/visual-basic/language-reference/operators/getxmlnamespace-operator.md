---
title: GetXmlNamespace İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786615"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="ab102-102">GetXmlNamespace İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab102-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="ab102-103">Alır <xref:System.Xml.Linq.XNamespace> belirtilen XML ad alanı öneki için karşılık gelen nesne.</span><span class="sxs-lookup"><span data-stu-id="ab102-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab102-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab102-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="ab102-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ab102-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="ab102-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ab102-106">Optional.</span></span> <span data-ttu-id="ab102-107">XML ad alanı öneki tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="ab102-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="ab102-108">Belirtilirse, bu dizenin geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab102-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="ab102-109">Daha fazla bilgi için [adları, bildirilmiş XML öğeleri ve özniteliklerinin](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ab102-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="ab102-110">Önek yok belirtilirse, varsayılan ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ab102-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="ab102-111">Boş ad alanı varsayılan ad alanı yok belirtilirse, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ab102-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab102-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab102-112">Return Value</span></span>  
 <span data-ttu-id="ab102-113"><xref:System.Xml.Linq.XNamespace> XML ad alanı öneki için karşılık gelen nesne.</span><span class="sxs-lookup"><span data-stu-id="ab102-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab102-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab102-114">Remarks</span></span>  
 <span data-ttu-id="ab102-115">`GetXmlNamespace` İşleci alır <xref:System.Xml.Linq.XNamespace> XML ad alanı öneki için karşılık gelen nesne `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="ab102-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="ab102-116">XML ad alanı öneklerini doğrudan XML sabit değerleri ve XML eksen özellikleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab102-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="ab102-117">Ancak, kullanmalısınız `GetXmlNamespace` işleci için bir ad alanı öneki dönüştürmek için bir <xref:System.Xml.Linq.XNamespace> kodunuzda kullanmadan önce nesne.</span><span class="sxs-lookup"><span data-stu-id="ab102-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="ab102-118">Bir nitelenmemiş öğe adı için eklediğiniz bir <xref:System.Xml.Linq.XNamespace> tam alınacak nesne <xref:System.Xml.Linq.XName> nesnesi, hangi çok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ab102-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab102-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab102-119">Example</span></span>  
 <span data-ttu-id="ab102-120">Aşağıdaki örnek alır `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="ab102-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ab102-121">XML değişmez değer oluşturmak ve bir nitelenmiş ada sahip ilk alt düğüm erişmek için bir ad alanı öneki kullanır `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="ab102-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="ab102-122">Daha sonra bu alt düğüme geçirir `ShowName` kullanarak tam bir ad oluşturur alt yordam `GetXmlNamespace` işleci.</span><span class="sxs-lookup"><span data-stu-id="ab102-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="ab102-123">`ShowName` Alt yordam daha sonra tam adı için geçirir <xref:System.Xml.Linq.XNode.Ancestors%2A> üst almak için yöntemi `ns:contact` düğümü.</span><span class="sxs-lookup"><span data-stu-id="ab102-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="ab102-124">Çağırdığınızda `TestGetXmlNamespace.RunSample()`, aşağıdaki metni içeren bir ileti kutusu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ab102-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="ab102-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab102-125">See Also</span></span>  
 [<span data-ttu-id="ab102-126">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="ab102-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="ab102-127">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="ab102-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
