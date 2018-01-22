---
title: "XSLT güvenlik konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7388bbc388dd46a30486a2300150bc9d1566593e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-security-considerations"></a><span data-ttu-id="0e329-102">XSLT güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="0e329-102">XSLT Security Considerations</span></span>
<span data-ttu-id="0e329-103">XSLT dili gücü ve esnekliği büyük bir bölümünü size özellikleri zengin bir dizi var.</span><span class="sxs-lookup"><span data-stu-id="0e329-103">The XSLT language has a rich set of features that give you a great deal of power and flexibility.</span></span> <span data-ttu-id="0e329-104">Dış kaynak tarafından kullanışlı olsa da yararlanılabilir, birçok özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="0e329-104">It includes many features that, while useful, could also be exploited by outside sources.</span></span> <span data-ttu-id="0e329-105">XSLT güvenli bir şekilde kullanmak için XSLT kullanırken çıkabilecek güvenlik sorunlarını ve bu riskleri azaltmak için uygulayabileceğiniz temel stratejileri türlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e329-105">In order to use XSLT safely, you must understand the types of security issues that arise when using XSLT, and the basic strategies that you can employ to mitigate these risks.</span></span>  
  
## <a name="xslt-extensions"></a><span data-ttu-id="0e329-106">XSLT uzantıları</span><span class="sxs-lookup"><span data-stu-id="0e329-106">XSLT Extensions</span></span>  
 <span data-ttu-id="0e329-107">İki popüler XSLT uzantıları stil sayfası komut dosyası ve uzantısı nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="0e329-107">Two popular XSLT extensions are style sheet scripting and extension objects.</span></span> <span data-ttu-id="0e329-108">Bu uzantılar XSLT işlemcisine kod yürütmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="0e329-108">These extensions allow the XSLT processor to execute code.</span></span>  
  
-   <span data-ttu-id="0e329-109">Uzantı nesneleri XSL Dönüşümleri programlama özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e329-109">Extension objects add programming capabilities to XSL transformations.</span></span>  
  
-   <span data-ttu-id="0e329-110">Komut dosyaları katıştırılmış stil sayfası kullanımında `msxsl:script` uzantı öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e329-110">Scripts can be embedded in the style sheet using the `msxsl:script` extension element.</span></span>  
  
### <a name="extension-objects"></a><span data-ttu-id="0e329-111">Uzantı nesneleri</span><span class="sxs-lookup"><span data-stu-id="0e329-111">Extension Objects</span></span>  
 <span data-ttu-id="0e329-112">Uzantı nesneleri kullanarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e329-112">Extension objects are added using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="0e329-113">FullTrust izin kümesi uzantısı nesnelerinin desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0e329-113">The FullTrust permission set is required to support extension objects.</span></span> <span data-ttu-id="0e329-114">Bu uzantı nesne kodu çalıştırıldığında izinleri ayrıcalıkların gerçekleşmez sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e329-114">This ensures that elevation of permissions does not happen when extension object code is executed.</span></span> <span data-ttu-id="0e329-115">Çağrı girişimi <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> FullTrust izinlerini sonuçlarında oluşturulan bir güvenlik özel durumu olmadan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e329-115">Attempting to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method without FullTrust permissions results in a security exception being thrown.</span></span>  
  
### <a name="style-sheet-scripts"></a><span data-ttu-id="0e329-116">Stil sayfası komut dosyaları</span><span class="sxs-lookup"><span data-stu-id="0e329-116">Style Sheet Scripts</span></span>  
 <span data-ttu-id="0e329-117">Komut dosyaları katıştırılmış kullanarak bir stil sayfası `msxsl:script` uzantı öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e329-117">Scripts can be embedded in a style sheet using the `msxsl:script` extension element.</span></span> <span data-ttu-id="0e329-118">Komut dosyası desteği üzerinde isteğe bağlı bir özellik olan <xref:System.Xml.Xsl.XslCompiledTransform> varsayılan olarak devre dışıdır sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e329-118">Script support is an optional feature on the <xref:System.Xml.Xsl.XslCompiledTransform> class that is disabled by default.</span></span> <span data-ttu-id="0e329-119">Komut dosyası etkinleştirilebilir ayarlayarak <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliğine `true` ve geçirme <xref:System.Xml.Xsl.XsltSettings> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e329-119">Scripting can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="0e329-120">Kuralları</span><span class="sxs-lookup"><span data-stu-id="0e329-120">Guidelines</span></span>  
 <span data-ttu-id="0e329-121">Stil sayfası güvenilen bir kaynaktan geldiğinden, yalnızca komut dosyası etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0e329-121">Enable scripting only when the style sheet comes from a trusted source.</span></span> <span data-ttu-id="0e329-122">Stil sayfası kaynağı doğrulanamıyor veya stil sayfası güvenilen bir kaynaktan geliyor değil, geçirin `null` XSLT ayarları bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0e329-122">If you cannot verify the source of the style sheet, or if the style sheet does not come from a trusted source, pass in `null` for the XSLT settings argument.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0e329-123">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0e329-123">External Resources</span></span>  
 <span data-ttu-id="0e329-124">XSLT dili gibi özelliklere sahiptir `xsl:import`, `xsl:include`, veya `document()` işlevi, burada işlemci gereken URI başvuruları çözümlenemedi.</span><span class="sxs-lookup"><span data-stu-id="0e329-124">The XSLT language has features such as `xsl:import`, `xsl:include`, or the `document()` function, where the processor needs to resolve URI references.</span></span> <span data-ttu-id="0e329-125"><xref:System.Xml.XmlResolver> Sınıfı, dış kaynaklara çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e329-125">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="0e329-126">Dış kaynaklara aşağıdaki iki durumda da çözümlenmesi gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="0e329-126">External resources may need to be resolved in the following two cases:</span></span>  
  
-   <span data-ttu-id="0e329-127">Stil sayfası derlerken <xref:System.Xml.XmlResolver> için kullanılan `xsl:import` ve `xsl:include` çözümleme.</span><span class="sxs-lookup"><span data-stu-id="0e329-127">When compiling a style sheet, the <xref:System.Xml.XmlResolver> is used for `xsl:import` and `xsl:include` resolution.</span></span>  
  
-   <span data-ttu-id="0e329-128">Dönüşümün yürütürken <xref:System.Xml.XmlResolver> çözümlemek için kullanılan `document()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="0e329-128">When executing the transformation, the <xref:System.Xml.XmlResolver> is used to resolve the `document()` function.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e329-129">`document()` İşlevi devre dışı bırakılmış varsayılan olarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e329-129">The `document()` function is disabled by default on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="0e329-130">Bu özellik ayarlayarak etkinleştirilebilir <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliğine `true` ve geçirme <xref:System.Xml.Xsl.XsltSettings> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e329-130">This feature can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
 <span data-ttu-id="0e329-131"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, her dahil kabul aşırı bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak.</span><span class="sxs-lookup"><span data-stu-id="0e329-131">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods each include overloads that accept an <xref:System.Xml.XmlResolver> as one of its arguments.</span></span> <span data-ttu-id="0e329-132">Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile kimlik bilgileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e329-132">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="0e329-133">Kuralları</span><span class="sxs-lookup"><span data-stu-id="0e329-133">Guidelines</span></span>  
 <span data-ttu-id="0e329-134">Etkinleştirme `document()` yalnızca stil sayfası güvenilir bir kaynaktan geldiğinde işlev.</span><span class="sxs-lookup"><span data-stu-id="0e329-134">Enable the `document()` function only when the style sheet comes from a trusted source.</span></span>  
  
 <span data-ttu-id="0e329-135">Aşağıdaki listede zaman belirtmek isteyebilirsiniz açıklanmaktadır bir <xref:System.Xml.XmlResolver> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="0e329-135">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="0e329-136">XSLT işlemi bir ağ kaynağına erişimi gerekiyorsa, kimlik doğrulaması gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="0e329-136">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="0e329-137">XSLT işlem erişebileceği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> doğru izniyle ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e329-137">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="0e329-138">Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e329-138">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="0e329-139">Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları gidermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e329-139">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="0e329-140">Dış kaynak erişilen sağlamak istiyorsanız, belirtebilirsiniz `null` için <xref:System.Xml.XmlResolver> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0e329-140">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e329-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e329-141">See Also</span></span>  
 [<span data-ttu-id="0e329-142">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="0e329-142">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="0e329-143">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="0e329-143">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [<span data-ttu-id="0e329-144">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e329-144">Code Access Security</span></span>](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
