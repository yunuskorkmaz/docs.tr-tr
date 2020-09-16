---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: ff50cbb561f9da5ea0877ded1de6fd3d5c424a7e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555965"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="cf27e-102">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="cf27e-102">XSLT Extension Objects</span></span>
<span data-ttu-id="cf27e-103">Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf27e-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="cf27e-104">Uzantı nesneleri sınıfı tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="cf27e-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="cf27e-105">Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf27e-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="cf27e-106">Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf27e-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="cf27e-107">Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf27e-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="cf27e-108">XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine yöntemi kullanılarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf27e-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="cf27e-109">Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="cf27e-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf27e-110">Yöntemi çağırmak için FullTrust izin kümesi gereklidir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf27e-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="cf27e-111">Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf27e-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="cf27e-112">Uzantı nesnelerinden döndürülen veri türleri,,, ve ' nin dört temel XPath veri türünden biridir `number` `string` `Boolean` `node set` .</span><span class="sxs-lookup"><span data-stu-id="cf27e-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="cf27e-113">`params`Belirtilmemiş bir parametre sayısının geçirilmesine izin veren anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda sınıfı tarafından desteklenmemektedir <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="cf27e-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cf27e-114">Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları `params` doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cf27e-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="cf27e-115">Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="cf27e-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="cf27e-116">XSLT uzantı nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cf27e-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="cf27e-117">Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak Uzantı nesnesini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf27e-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="cf27e-118">Uzantı nesnesini stil sayfasından çağırın.</span><span class="sxs-lookup"><span data-stu-id="cf27e-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="cf27e-119"><xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="cf27e-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf27e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf27e-120">See also</span></span>

- [<span data-ttu-id="cf27e-121">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="cf27e-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="cf27e-122">XSLT Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="cf27e-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
