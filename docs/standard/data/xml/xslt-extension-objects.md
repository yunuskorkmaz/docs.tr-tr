---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2efe31ce8ece241bdfeb95687c5496c7ba0fd626
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615295"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="4da58-102">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="4da58-102">XSLT Extension Objects</span></span>
<span data-ttu-id="4da58-103">Uzantı nesneler, stil sayfaları genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4da58-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="4da58-104">Genişletme nesneleri tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4da58-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="4da58-105">Ekli komut dosyası yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4da58-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="4da58-106">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4da58-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="4da58-107">Stil sayfaları, daha küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4da58-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="4da58-108">XSLT genişletme nesneleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4da58-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="4da58-109">Bir tam adı ve ad alanı URI o anda uzantısı nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="4da58-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4da58-110">FullTrust izin kümesi çağrı için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4da58-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="4da58-111">Daha fazla bilgi için [kod erişim güvenliği](../../../../docs/framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4da58-111">For more information, see [Code Access Security](../../../../docs/framework/misc/code-access-security.md) and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4da58-112">Uzantı nesnelerinden döndürülen veri türleri dört temel XPath veri türlerinden biri: `number`, `string`, `Boolean`, ve `node set`.</span><span class="sxs-lookup"><span data-stu-id="4da58-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="4da58-113">Herhangi bir yöntemi ile tanımlanmış `params` geçirilecek parametreler belirtilmemiş bir sayısını veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4da58-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4da58-114">Herhangi bir yöntemi ile tanımlanmış yazılımınız XSLT stil sayfalarını `params` anahtar sözcüğü doğru şekilde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4da58-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="4da58-115">Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="4da58-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="4da58-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="4da58-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="4da58-117">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve uzantısını kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4da58-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="4da58-118">Uzantı nesnesi stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="4da58-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="4da58-119">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4da58-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da58-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4da58-120">See also</span></span>

- [<span data-ttu-id="4da58-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4da58-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="4da58-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="4da58-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
