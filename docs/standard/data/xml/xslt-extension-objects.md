---
title: XSLT uzantısı nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69fcd4bd8426bb349c090fc52f7a1f1a262378ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570585"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="6df24-102">XSLT uzantısı nesneleri</span><span class="sxs-lookup"><span data-stu-id="6df24-102">XSLT Extension Objects</span></span>
<span data-ttu-id="6df24-103">Uzantı nesneler, stil sayfaları işlevselliğini genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6df24-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="6df24-104">Uzantı nesneleri tarafından korunduğundan <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6df24-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="6df24-105">Katıştırılmış betik yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6df24-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="6df24-106">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df24-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="6df24-107">Stil sayfaları, küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df24-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="6df24-108">XSLT uzantısı nesnelerinin eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df24-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="6df24-109">Bir tam adı ve ad alanı URI'si o anda uzantısı nesne ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="6df24-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6df24-110">FullTrust izin kümesi çağırmak için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df24-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="6df24-111">Daha fazla bilgi için bkz: [kod erişim güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) ve [NIB: adlandırılmış izin kümeleri](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="6df24-111">For more information, see [Code Access Security](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="6df24-112">Dört temel XPath veri türlerinden birini uzantısı nesnelerden döndürülen veri türleri: `number`, `string`, `Boolean`, ve `node set`.</span><span class="sxs-lookup"><span data-stu-id="6df24-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="6df24-113">İle tanımlanmış herhangi bir yöntemini `params` belirsiz sayıda iletilecek parametre veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6df24-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="6df24-114">İle tanımlanmış herhangi bir yöntemini kullanan XSLT stil sayfaları `params` anahtar sözcüğü düzgün çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6df24-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="6df24-115">Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="6df24-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="6df24-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6df24-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="6df24-117">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesnesini ve nesne uzantısını kullanarak ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df24-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="6df24-118">Uzantı nesnesi stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="6df24-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="6df24-119">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df24-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df24-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6df24-120">See Also</span></span>  
 [<span data-ttu-id="6df24-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6df24-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="6df24-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="6df24-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
