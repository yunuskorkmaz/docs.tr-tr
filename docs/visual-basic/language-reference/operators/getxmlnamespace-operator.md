---
title: "GetXmlNamespace İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="9aeb2-102">GetXmlNamespace İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aeb2-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="9aeb2-103">Alır <xref:System.Xml.Linq.XNamespace> için belirtilen XML ad alanı öneki karşılık gelen nesne.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aeb2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9aeb2-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="9aeb2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9aeb2-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="9aeb2-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-106">Optional.</span></span> <span data-ttu-id="9aeb2-107">XML ad alanı öneki tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="9aeb2-108">Sağlanan bu dizenin geçerli bir XML tanımlayıcısı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="9aeb2-109">Daha fazla bilgi için bkz: [adları bildirilmiş XML öğeleri ve öznitelikleri](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9aeb2-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="9aeb2-110">Önek belirtilmezse, varsayılan ad alanını döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="9aeb2-111">Varsayılan ad alanı belirtilmezse, boş ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aeb2-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9aeb2-112">Return Value</span></span>  
 <span data-ttu-id="9aeb2-113"><xref:System.Xml.Linq.XNamespace> İçin XML ad alanı öneki karşılık gelen nesne.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aeb2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aeb2-114">Remarks</span></span>  
 <span data-ttu-id="9aeb2-115">`GetXmlNamespace` İşleci alır <xref:System.Xml.Linq.XNamespace> için XML ad alanı öneki karşılık gelen nesne `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="9aeb2-116">XML ad alanı önekleri doğrudan XML değişmez değerleri ve XML eksen özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="9aeb2-117">Ancak, kullanmalıdır `GetXmlNamespace` işleci için bir ad alanı öneki dönüştürmek için bir <xref:System.Xml.Linq.XNamespace> kodunuzda kullanabilmeniz için önce nesne.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="9aeb2-118">Nitelenmemiş öğe adı için ekleyebilirsiniz bir <xref:System.Xml.Linq.XNamespace> nesnesi tam olarak nitelenmiş <xref:System.Xml.Linq.XName> nesnesi, hangi çok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aeb2-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aeb2-119">Example</span></span>  
 <span data-ttu-id="9aeb2-120">Aşağıdaki örnek alır `ns` bir XML ad alanı öneki olarak.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="9aeb2-121">XML değişmez değer oluşturmak ve tam adına sahip ilk alt düğüm erişmek için ad alanı öneki sonra kullanan `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="9aeb2-122">Daha sonra bu alt düğüme geçirir `ShowName` kullanarak bir tam ad yapıları alt yordama `GetXmlNamespace` işleci.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="9aeb2-123">`ShowName` Alt yordama daha sonra tam adı geçirir <xref:System.Xml.Linq.XNode.Ancestors%2A> üst almak için yöntemi `ns:contact` düğümü.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="9aeb2-124">Çağırdığınızda `TestGetXmlNamespace.RunSample()`, aşağıdaki metni içeren bir ileti kutusu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="9aeb2-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="9aeb2-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aeb2-125">See Also</span></span>  
 [<span data-ttu-id="9aeb2-126">Imports deyimi (XML Namespace)</span><span class="sxs-lookup"><span data-stu-id="9aeb2-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="9aeb2-127">Visual Basic'de XML'e erişme</span><span class="sxs-lookup"><span data-stu-id="9aeb2-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
