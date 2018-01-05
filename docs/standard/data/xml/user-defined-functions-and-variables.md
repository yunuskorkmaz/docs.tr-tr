---
title: "Kullanıcı tanımlı işlevler ve değişkenler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6870861541a063c56f83dcb286d21a5a970d1b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="94bb9-102">Kullanıcı tanımlı işlevler ve değişkenler</span><span class="sxs-lookup"><span data-stu-id="94bb9-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="94bb9-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı ile etkileşim kurmak için kullanılan yöntemler kümesi sağlar <xref:System.Xml.XPath.XPathDocument> veri.</span><span class="sxs-lookup"><span data-stu-id="94bb9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="94bb9-104">XPath sorgusu ifadeleri tarafından uzantısı işlevleri ve değişkenler kullanmak için uygulayarak standart XPath işlevleri destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94bb9-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="94bb9-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> Yöntemi türetilmiş bir kullanıcı tanımlı içerik kabul edebileceği <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="94bb9-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="94bb9-106">Kullanıcı tanımlı işlevler özel bağlam tarafından çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="94bb9-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="94bb9-107">Uzantı işlevleri ve değişkenler XML ekleme saldırıları önleme yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="94bb9-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="94bb9-108">Bu senaryolarda kullanıcı girişi özel değişkenleri için atanan ve işlem yönergeleri ile birleştirilmiş değil raw giriş olarak uzantısı işlevleri tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="94bb9-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="94bb9-109">Bunu yalnızca XML verileri üzerinde tasarımcı tarafından istendiği gibi üstlenebilir uzantı işlevleri ve değişkenler kullanıcı girişi içerir.</span><span class="sxs-lookup"><span data-stu-id="94bb9-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="94bb9-110">Uzantıları kullanmak için özel bir uygulama <xref:System.Xml.Xsl.XsltContext> arabirimler birlikte sınıfı <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantısı işlevleri ve değişkenler destekler.</span><span class="sxs-lookup"><span data-stu-id="94bb9-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="94bb9-111">Bir <xref:System.Xml.XPath.XPathExpression> ile kullanıcı girişi ekler, <xref:System.Xml.Xsl.XsltArgumentList> özel <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="94bb9-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="94bb9-112"><xref:System.Xml.XPath.XPathExpression> Bir derlenmiş temsil eden sorgu <xref:System.Xml.XPath.XPathNavigator> bulmak ve ifade tarafından tanımlanan düğümleri işlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="94bb9-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="94bb9-113">Aşağıdaki örnek, uygulama özel bağlamı sınıfının türetilen gösterir <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="94bb9-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="94bb9-114">Kod açıklamaları sınıf üyeleri ve kullanımlarını özel işlevlerinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94bb9-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="94bb9-115">Bu kod kesimi işlevi ve değişken uygulamaları ve bu uygulamaları kullanan örnek bir uygulama izleyin.</span><span class="sxs-lookup"><span data-stu-id="94bb9-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="94bb9-116">Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="94bb9-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="94bb9-117">Uygulayan sınıfa <xref:System.Xml.Xsl.IXsltContextFunction> çözümler ve kullanıcı tanımlı işlevler yürütür.</span><span class="sxs-lookup"><span data-stu-id="94bb9-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="94bb9-118">Bu örnek bildirimi tarafından tanımlanan işlevi kullanır: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="94bb9-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="94bb9-119">Kod açıklamaları sınıf üyeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94bb9-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="94bb9-120">Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="94bb9-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="94bb9-121">Bu sınıf, çalışma zamanında kullanıcı tarafından tanımlanan değişkenler XPath sorgu ifadelerinde başvuru çözümler.</span><span class="sxs-lookup"><span data-stu-id="94bb9-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="94bb9-122">Bu sınıfın bir örneği oluşturulur ve geçersiz kılınan tarafından döndürülen <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> yöntemi özel <xref:System.Xml.Xsl.XsltContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="94bb9-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="94bb9-123">Kod açıklamaları sınıf üyeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94bb9-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="94bb9-124">Kapsamdaki önceki sınıf tanımlarını aşağıdaki kod öğelerini karakter sayısı için özel işlevi kullanır `Tasks.xml` belge.</span><span class="sxs-lookup"><span data-stu-id="94bb9-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="94bb9-125">Kod açıklamaları açıklayan özel işlevi derler ve karşı çalışan kod `Tasks.xml` belge.</span><span class="sxs-lookup"><span data-stu-id="94bb9-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="94bb9-126">Bu örnekte aşağıdaki XML verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="94bb9-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
