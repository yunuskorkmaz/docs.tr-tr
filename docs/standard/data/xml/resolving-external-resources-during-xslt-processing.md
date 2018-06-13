---
title: Dış kaynaklara XSLT işleme sırasında çözme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 955b42a4bb9955a401265cf9537418bbfe8dd7c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569765"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="566e8-102">Dış kaynaklara XSLT işleme sırasında çözme</span><span class="sxs-lookup"><span data-stu-id="566e8-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="566e8-103">Alırken birkaç kez XSLT dönüştürmesi sırasında dış kaynaklara çözmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="566e8-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="566e8-104">XmlResolver sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="566e8-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="566e8-105"><xref:System.Xml.XmlResolver> Sınıfı, dış kaynaklara çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="566e8-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="566e8-106">Aşağıdaki tabloda ne zaman açıklanmaktadır <xref:System.Xml.XmlResolver> XSLT işleme sırasında söz konusu olur.</span><span class="sxs-lookup"><span data-stu-id="566e8-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="566e8-107">XSLT görevi</span><span class="sxs-lookup"><span data-stu-id="566e8-107">XSLT task</span></span>|<span data-ttu-id="566e8-108">XmlResolver için kullanılır</span><span class="sxs-lookup"><span data-stu-id="566e8-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="566e8-109">Stil sayfası derleyin.</span><span class="sxs-lookup"><span data-stu-id="566e8-109">Compile the style sheet.</span></span>|<span data-ttu-id="566e8-110">Stil sayfası URI'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="566e8-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="566e8-111">- ve -</span><span class="sxs-lookup"><span data-stu-id="566e8-111">-and-</span></span><br /><br /> <span data-ttu-id="566e8-112">Herhangi bir URI başvuruları çözümlenemedi `xsl:import` veya `xsl:include` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="566e8-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="566e8-113">Stil sayfasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="566e8-113">Execute the style sheet.</span></span>|<span data-ttu-id="566e8-114">Bağlam belge URI'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="566e8-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="566e8-115">- ve -</span><span class="sxs-lookup"><span data-stu-id="566e8-115">-and-</span></span><br /><br /> <span data-ttu-id="566e8-116">Tüm XSLT URI başvuruları çözümleyin `document()` işlevleri.</span><span class="sxs-lookup"><span data-stu-id="566e8-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="566e8-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri dahil almak aşırı bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="566e8-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="566e8-118">Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile kimlik bilgileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="566e8-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="566e8-119">Aşağıdaki listede zaman belirtmek isteyebilirsiniz açıklanmaktadır bir <xref:System.Xml.XmlResolver> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="566e8-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="566e8-120">XSLT işlemi bir ağ kaynağına erişimi gerekiyorsa, kimlik doğrulaması gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="566e8-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="566e8-121">XSLT işlem erişebileceği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> doğru izniyle ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="566e8-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="566e8-122">Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.</span><span class="sxs-lookup"><span data-stu-id="566e8-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="566e8-123">Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları gidermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="566e8-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="566e8-124">Dış kaynak erişilen sağlamak istiyorsanız, belirtebilirsiniz `null` için <xref:System.Xml.XmlResolver> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="566e8-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="566e8-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="566e8-125">Example</span></span>  
 <span data-ttu-id="566e8-126">Aşağıdaki örnek, bir ağ kaynağına depolanan bir stil sayfası derler.</span><span class="sxs-lookup"><span data-stu-id="566e8-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="566e8-127">Bir <xref:System.Xml.XmlUrlResolver> nesne stil sayfası erişmek gereken kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="566e8-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="566e8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="566e8-128">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [<span data-ttu-id="566e8-129">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="566e8-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
