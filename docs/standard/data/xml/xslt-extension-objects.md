---
title: XSLT genişletme nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f958af5859804cdeb382adab2f3772c42ac5b16
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483969"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="e0c57-102">XSLT genişletme nesneleri</span><span class="sxs-lookup"><span data-stu-id="e0c57-102">XSLT Extension Objects</span></span>
<span data-ttu-id="e0c57-103">Uzantı nesneler, stil sayfaları genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0c57-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="e0c57-104">Genişletme nesneleri tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0c57-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="e0c57-105">Ekli komut dosyası yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e0c57-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="e0c57-106">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0c57-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="e0c57-107">Stil sayfaları, daha küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0c57-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="e0c57-108">XSLT genişletme nesneleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0c57-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="e0c57-109">Bir tam adı ve ad alanı URI o anda uzantısı nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e0c57-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0c57-110">FullTrust izin kümesi çağrı için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0c57-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="e0c57-111">Daha fazla bilgi için [kod erişim güvenliği](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) ve [NIB: adlandırılmış izin kümeleri](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="e0c57-111">For more information, see [Code Access Security](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="e0c57-112">Uzantı nesnelerinden döndürülen veri türleri dört temel XPath veri türlerinden biri: `number`, `string`, `Boolean`, ve `node set`.</span><span class="sxs-lookup"><span data-stu-id="e0c57-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="e0c57-113">Herhangi bir yöntemi ile tanımlanmış `params` geçirilecek parametreler belirtilmemiş bir sayısını veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0c57-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e0c57-114">Herhangi bir yöntemi ile tanımlanmış yazılımınız XSLT stil sayfalarını `params` anahtar sözcüğü doğru şekilde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e0c57-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="e0c57-115">Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="e0c57-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="e0c57-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e0c57-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="e0c57-117">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve uzantısını kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0c57-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="e0c57-118">Uzantı nesnesi stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="e0c57-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="e0c57-119">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0c57-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c57-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c57-120">See Also</span></span>  
 [<span data-ttu-id="e0c57-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e0c57-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="e0c57-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="e0c57-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
