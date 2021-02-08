---
description: 'Hakkında daha fazla bilgi edinin: Kullanıcı tanımlı Işlevler ve değişkenler'
title: Kullanıcı Tanımlı İşlevler ve Değişkenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: 730f99b1d8b9cefafbdff4ed74b9775b0be863c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782864"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="08e26-103">Kullanıcı Tanımlı İşlevler ve Değişkenler</span><span class="sxs-lookup"><span data-stu-id="08e26-103">User Defined Functions and Variables</span></span>

<span data-ttu-id="08e26-104"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, verilerle etkileşim kurmak için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="08e26-104">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="08e26-105">XPath sorgu ifadeleri tarafından kullanılmak üzere uzantı işlevleri ve değişkenler uygulayarak standart XPath işlevlerini tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08e26-105">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="08e26-106"><xref:System.Xml.XPath.XPathExpression.SetContext%2A>Yöntemi öğesinden türetilmiş Kullanıcı tanımlı bir bağlamı kabul edebilir <xref:System.Xml.Xsl.XsltContext> .</span><span class="sxs-lookup"><span data-stu-id="08e26-106">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="08e26-107">Kullanıcı tanımlı işlevler özel bağlam tarafından çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="08e26-107">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="08e26-108">Uzantı işlevleri ve değişkenler, XML ekleme saldırılarını önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="08e26-108">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="08e26-109">Bu senaryolarda, Kullanıcı girişi özel değişkenlere atanır ve işlem yönergeleriyle birleştirilmiş ham giriş olarak değil uzantı işlevleri tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="08e26-109">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="08e26-110">Uzantı işlevleri ve değişkenler, yalnızca tasarımcı tarafından amaçlanan XML verilerinde davranması için Kullanıcı girişi içerir.</span><span class="sxs-lookup"><span data-stu-id="08e26-110">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="08e26-111">Uzantıları kullanmak için <xref:System.Xml.Xsl.XsltContext> , arabirimler ile birlikte özel bir sınıf uygulayın <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantı işlevlerini ve değişkenlerini destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08e26-111">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="08e26-112">, <xref:System.Xml.XPath.XPathExpression> Kendi özel öğesine sahip kullanıcı girişi ekler <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltContext> .</span><span class="sxs-lookup"><span data-stu-id="08e26-112">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="08e26-113">, <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathNavigator> İfadesi tarafından tanımlanan düğümleri bulmak ve işlemek için kullanılan bir derlenmiş sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="08e26-113">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="08e26-114">Aşağıdaki örnek, öğesinden türetilmiş özel bir bağlam sınıfının uygulamasını gösterir <xref:System.Xml.Xsl.XsltContext> .</span><span class="sxs-lookup"><span data-stu-id="08e26-114">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="08e26-115">Koddaki açıklamalar sınıf üyelerini ve bunların özel işlevlerde kullanımını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08e26-115">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="08e26-116">İşlev ve değişken uygulamaları ve bu uygulamaları kullanan bir örnek uygulama bu kod segmentini izler.</span><span class="sxs-lookup"><span data-stu-id="08e26-116">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="08e26-117">Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextFunction> .</span><span class="sxs-lookup"><span data-stu-id="08e26-117">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="08e26-118">Uygulayan sınıf, <xref:System.Xml.Xsl.IXsltContextFunction> Kullanıcı tanımlı işlevleri çözer ve yürütür.</span><span class="sxs-lookup"><span data-stu-id="08e26-118">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="08e26-119">Bu örnek, bildirimi tarafından tanımlanan işlevi kullanır: `private int CountChar(string title, char charTocount)` .</span><span class="sxs-lookup"><span data-stu-id="08e26-119">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="08e26-120">Kod açıklamaları sınıf üyelerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08e26-120">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="08e26-121">Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextVariable> .</span><span class="sxs-lookup"><span data-stu-id="08e26-121">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="08e26-122">Bu sınıf, çalışma zamanında XPath sorgu ifadelerinde Kullanıcı tanımlı değişkenlere yapılan başvuruları çözümler.</span><span class="sxs-lookup"><span data-stu-id="08e26-122">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="08e26-123">Bu sınıfın bir örneği oluşturulur ve özel sınıfın geçersiz kılınan yöntemiyle döndürülür <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> <xref:System.Xml.Xsl.XsltContext> .</span><span class="sxs-lookup"><span data-stu-id="08e26-123">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="08e26-124">Kod açıklamaları sınıf üyelerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08e26-124">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="08e26-125">Kapsamdaki önceki sınıf tanımlarıyla aşağıdaki kod, belgenin öğelerindeki karakterleri saymak için özel fonksiyonunu kullanır `Tasks.xml` .</span><span class="sxs-lookup"><span data-stu-id="08e26-125">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="08e26-126">Koddaki açıklamalar, özel işlevi derleyen ve belgeye karşı çalışan kodu anlatmaktadır `Tasks.xml` .</span><span class="sxs-lookup"><span data-stu-id="08e26-126">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="08e26-127">Bu örnek, aşağıdaki XML verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="08e26-127">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
