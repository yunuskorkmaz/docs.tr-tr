---
title: XSLT İşleme Sırasında Dış Kaynakları Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bcd45a97ab0f0b0ac462d50c18fb68f9d7bd386
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590021"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="f12b7-102">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="f12b7-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="f12b7-103">Bazı birkaç kez XSLT dönüştürmesi sırasında dış kaynakları çözümleme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f12b7-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="f12b7-104">XmlResolver sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="f12b7-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="f12b7-105"><xref:System.Xml.XmlResolver> Sınıfı dış kaynakları çözümleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f12b7-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="f12b7-106">Aşağıdaki tabloda, ne zaman açıklanmaktadır <xref:System.Xml.XmlResolver> XSLT işleme sırasında ilgili hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f12b7-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="f12b7-107">XSLT görevi</span><span class="sxs-lookup"><span data-stu-id="f12b7-107">XSLT task</span></span>|<span data-ttu-id="f12b7-108">XmlResolver ne için kullanılır</span><span class="sxs-lookup"><span data-stu-id="f12b7-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="f12b7-109">Stil sayfası derleyin.</span><span class="sxs-lookup"><span data-stu-id="f12b7-109">Compile the style sheet.</span></span>|<span data-ttu-id="f12b7-110">Stil Sayfası URI çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="f12b7-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="f12b7-111">- ve -</span><span class="sxs-lookup"><span data-stu-id="f12b7-111">-and-</span></span><br /><br /> <span data-ttu-id="f12b7-112">Herhangi bir URI başvuruları çözümlemek `xsl:import` veya `xsl:include` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f12b7-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="f12b7-113">Stil sayfası yürütün.</span><span class="sxs-lookup"><span data-stu-id="f12b7-113">Execute the style sheet.</span></span>|<span data-ttu-id="f12b7-114">Bağlam belge URI'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="f12b7-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="f12b7-115">- ve -</span><span class="sxs-lookup"><span data-stu-id="f12b7-115">-and-</span></span><br /><br /> <span data-ttu-id="f12b7-116">Tüm XSLT URI başvuruları çözümlemek `document()` işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f12b7-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="f12b7-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri dahil olması aşırı yüklemeler bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f12b7-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="f12b7-118">Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile herhangi bir kimlik bilgisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f12b7-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="f12b7-119">Aşağıdaki listede, ne zaman belirtmek isteyebilirsiniz açıklar bir <xref:System.Xml.XmlResolver> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="f12b7-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="f12b7-120">XSLT işlemi bir ağ kaynağına erişmesi gerekiyorsa, kimlik doğrulama gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle.</span><span class="sxs-lookup"><span data-stu-id="f12b7-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="f12b7-121">XSLT işlemi erişebildiği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> ile doğru izni ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f12b7-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="f12b7-122">Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f12b7-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="f12b7-123">Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları çözümlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f12b7-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="f12b7-124">Belirtebileceğiniz hiçbir dış kaynaklara erişildiğini sağlamak istiyorsanız, `null` için <xref:System.Xml.XmlResolver> bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="f12b7-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f12b7-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f12b7-125">Example</span></span>  
 <span data-ttu-id="f12b7-126">Aşağıdaki örnek, bir ağ kaynakta depolanan bir stil sayfası derler.</span><span class="sxs-lookup"><span data-stu-id="f12b7-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="f12b7-127">Bir <xref:System.Xml.XmlUrlResolver> nesnesini stil sayfası erişmek gereken kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f12b7-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f12b7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f12b7-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="f12b7-129">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f12b7-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
