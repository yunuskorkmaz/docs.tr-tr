---
description: 'Daha fazla bilgi edinin: XSLT uzantı nesneleri'
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 5fc4ee8b3828219bc298a3ffc4c81bc342e2f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782539"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="99eca-103">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="99eca-103">XSLT Extension Objects</span></span>

<span data-ttu-id="99eca-104">Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99eca-104">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="99eca-105">Uzantı nesneleri sınıfı tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="99eca-105">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="99eca-106">Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99eca-106">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="99eca-107">Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="99eca-107">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="99eca-108">Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="99eca-108">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="99eca-109">XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine yöntemi kullanılarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="99eca-109">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="99eca-110">Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="99eca-110">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99eca-111">Yöntemi çağırmak için FullTrust izin kümesi gereklidir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="99eca-111">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="99eca-112">Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="99eca-112">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="99eca-113">Uzantı nesnelerinden döndürülen veri türleri,,, ve ' nin dört temel XPath veri türünden biridir `number` `string` `Boolean` `node set` .</span><span class="sxs-lookup"><span data-stu-id="99eca-113">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="99eca-114">`params`Belirtilmemiş bir parametre sayısının geçirilmesine izin veren anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda sınıfı tarafından desteklenmemektedir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="99eca-114">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="99eca-115">Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları `params` doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="99eca-115">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="99eca-116">Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="99eca-116">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="99eca-117">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="99eca-117">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="99eca-118">Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak Uzantı nesnesini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="99eca-118">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="99eca-119">Uzantı nesnesini stil sayfasından çağırın.</span><span class="sxs-lookup"><span data-stu-id="99eca-119">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="99eca-120"><xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="99eca-120">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99eca-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99eca-121">See also</span></span>

- [<span data-ttu-id="99eca-122">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="99eca-122">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="99eca-123">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="99eca-123">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
