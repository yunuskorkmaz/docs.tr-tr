---
title: "XSLT uzantısı nesneleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f7d80bc67257afeaa131b4e356cb378d21f684e0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="8c327-102">XSLT uzantısı nesneleri</span><span class="sxs-lookup"><span data-stu-id="8c327-102">XSLT Extension Objects</span></span>
<span data-ttu-id="8c327-103">Uzantı nesneler, stil sayfaları işlevselliğini genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c327-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="8c327-104">Uzantı nesneleri tarafından korunduğundan <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c327-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="8c327-105">Katıştırılmış betik yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8c327-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="8c327-106">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c327-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="8c327-107">Stil sayfaları, küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c327-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="8c327-108">XSLT uzantısı nesnelerinin eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c327-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="8c327-109">Bir tam adı ve ad alanı URI'si o anda uzantısı nesne ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="8c327-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c327-110">FullTrust izin kümesi çağırmak için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c327-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="8c327-111">Daha fazla bilgi için bkz: [kod erişim güvenliği](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) ve [NIB: adlandırılmış izin kümeleri](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="8c327-111">For more information, see [Code Access Security](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="8c327-112">Dört temel XPath veri türlerinden birini uzantısı nesnelerden döndürülen veri türleri: `number`, `string`, `Boolean`, ve `node set`.</span><span class="sxs-lookup"><span data-stu-id="8c327-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="8c327-113">İle tanımlanmış herhangi bir yöntemini `params` belirsiz sayıda iletilecek parametre veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c327-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8c327-114">İle tanımlanmış herhangi bir yöntemini kullanan XSLT stil sayfaları `params` anahtar sözcüğü düzgün çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="8c327-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="8c327-115">Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="8c327-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="8c327-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8c327-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="8c327-117">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesnesini ve nesne uzantısını kullanarak ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c327-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="8c327-118">Uzantı nesnesi stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="8c327-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="8c327-119">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c327-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c327-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c327-120">See Also</span></span>  
 [<span data-ttu-id="8c327-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="8c327-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="8c327-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="8c327-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
