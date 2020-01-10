---
title: XSLT İşleme Sırasında Dış Kaynakları Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710290"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="baaa5-102">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="baaa5-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="baaa5-103">Dış kaynakları çözmeniz gerekebilmeniz için bir XSLT dönüştürmesi sırasında birkaç zaman vardır.</span><span class="sxs-lookup"><span data-stu-id="baaa5-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="baaa5-104">XmlResolver sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="baaa5-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="baaa5-105"><xref:System.Xml.XmlResolver> sınıfı, dış kaynakları çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baaa5-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="baaa5-106">Aşağıdaki tabloda XSLT işleme sırasında <xref:System.Xml.XmlResolver> ne zaman dahil olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="baaa5-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="baaa5-107">XSLT görevi</span><span class="sxs-lookup"><span data-stu-id="baaa5-107">XSLT task</span></span>|<span data-ttu-id="baaa5-108">İçin XmlResolver kullanılma</span><span class="sxs-lookup"><span data-stu-id="baaa5-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="baaa5-109">Stil sayfasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="baaa5-109">Compile the style sheet.</span></span>|<span data-ttu-id="baaa5-110">Stil sayfasının URI 'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="baaa5-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="baaa5-111">\- ve -</span><span class="sxs-lookup"><span data-stu-id="baaa5-111">-and-</span></span><br /><br /> <span data-ttu-id="baaa5-112">Herhangi bir `xsl:import` veya `xsl:include` öğesinde URI başvurularını çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="baaa5-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="baaa5-113">Stil sayfasını yürütün.</span><span class="sxs-lookup"><span data-stu-id="baaa5-113">Execute the style sheet.</span></span>|<span data-ttu-id="baaa5-114">Bağlam belgesinin URI 'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="baaa5-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="baaa5-115">\- ve -</span><span class="sxs-lookup"><span data-stu-id="baaa5-115">-and-</span></span><br /><br /> <span data-ttu-id="baaa5-116">Tüm XSLT `document()` işlevlerinde URI başvurularını çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="baaa5-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="baaa5-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, bağımsız değişkenlerinden biri olarak bir <xref:System.Xml.XmlResolver> nesnesi alan aşırı yüklemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="baaa5-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="baaa5-118">Bir <xref:System.Xml.XmlResolver> belirtilmemişse, kimlik bilgileri olmayan bir varsayılan <xref:System.Xml.XmlUrlResolver> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baaa5-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="baaa5-119">Aşağıdaki listede bir <xref:System.Xml.XmlResolver> nesnesi belirtmek isteyebileceğiniz zaman açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="baaa5-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="baaa5-120">XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, gerekli kimlik bilgileriyle bir <xref:System.Xml.XmlResolver> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baaa5-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="baaa5-121">XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, doğru izin kümesiyle bir <xref:System.Xml.XmlSecureResolver> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baaa5-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="baaa5-122">Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa <xref:System.Xml.XmlSecureResolver> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="baaa5-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="baaa5-123">Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baaa5-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="baaa5-124">Dış kaynaklara erişilmemesini sağlamak istiyorsanız <xref:System.Xml.XmlResolver> bağımsız değişkeni için `null` belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baaa5-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baaa5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="baaa5-125">Example</span></span>  
 <span data-ttu-id="baaa5-126">Aşağıdaki örnek, bir ağ kaynağında depolanan bir stil sayfasını derler.</span><span class="sxs-lookup"><span data-stu-id="baaa5-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="baaa5-127"><xref:System.Xml.XmlUrlResolver> nesnesi, stil sayfasına erişmek için gereken kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baaa5-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="baaa5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baaa5-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="baaa5-129">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="baaa5-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
