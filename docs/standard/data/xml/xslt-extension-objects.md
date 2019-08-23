---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924934"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="96384-102">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="96384-102">XSLT Extension Objects</span></span>
<span data-ttu-id="96384-103">Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96384-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="96384-104">Uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> sınıfı tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="96384-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="96384-105">Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="96384-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="96384-106">Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96384-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="96384-107">Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96384-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="96384-108">XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi kullanılarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="96384-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="96384-109">Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="96384-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96384-110"><xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> Yöntemi çağırmak için FullTrust izin kümesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96384-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="96384-111">Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../../docs/framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="96384-111">For more information, see [Code Access Security](../../../../docs/framework/misc/code-access-security.md) and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="96384-112">Uzantı nesnelerinden döndürülen `number`veri türleri `Boolean`, `string`,, ve `node set`' nin dört temel XPath veri türünden biridir.</span><span class="sxs-lookup"><span data-stu-id="96384-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="96384-113">Belirtilmemiş bir parametre sayısının geçirilmesine izin veren `params` anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı tarafından desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="96384-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="96384-114">`params` Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="96384-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="96384-115">Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="96384-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="96384-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="96384-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="96384-117">Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> Uzantı nesnesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96384-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="96384-118">Uzantı nesnesini stil sayfasından çağırın.</span><span class="sxs-lookup"><span data-stu-id="96384-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="96384-119"><xref:System.Xml.Xsl.XsltArgumentList> Nesneyi<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="96384-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96384-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96384-120">See also</span></span>

- [<span data-ttu-id="96384-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="96384-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="96384-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="96384-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
