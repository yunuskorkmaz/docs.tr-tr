---
title: System.Uri ad alanında sürümü 2.0 yapılan değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 169454edd04bfdb55affcc2be12140f42dd2f7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392454"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="e278a-102">System.Uri ad alanında sürümü 2.0 yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e278a-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="e278a-103">Birkaç değişiklik yapılan <xref:System.Uri?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e278a-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e278a-104">Bu değişiklikler yanlış davranışa sabit, kullanılabilirlik ve geliştirilmiş Gelişmiş Güvenlik.</span><span class="sxs-lookup"><span data-stu-id="e278a-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="e278a-105">Artık kullanılmayan ve kullanım dışı üyeleri</span><span class="sxs-lookup"><span data-stu-id="e278a-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="e278a-106">Oluşturucular:</span><span class="sxs-lookup"><span data-stu-id="e278a-106">Constructors:</span></span>  
  
-   <span data-ttu-id="e278a-107">Sahip tüm oluşturucular bir `dontEscape` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e278a-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="e278a-108">Yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="e278a-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="e278a-109">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e278a-109">Changes</span></span>  
  
-   <span data-ttu-id="e278a-110">(Dosya, ftp ve diğerleri), sorgu parçası almamayı bilinen URI şemaları için '?' karakteri her zaman Atlanan ve başlangıcı sayılmaz bir <xref:System.Uri.Query%2A> bölümü.</span><span class="sxs-lookup"><span data-stu-id="e278a-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="e278a-111">Örtük dosyası URI'ler için (formun "c:\directory\file@name.txt"), tam unescaping istenen sürece parça karakteri ('#') her zaman Atlanan veya <xref:System.Uri.LocalPath%2A> olan `true`.</span><span class="sxs-lookup"><span data-stu-id="e278a-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="e278a-112">UNC hostname Desteği kaldırılmıştır; Uluslararası ana bilgisayar adları temsil etmek için IDN belirtimi benimsenen.</span><span class="sxs-lookup"><span data-stu-id="e278a-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="e278a-113"><xref:System.Uri.LocalPath%2A> her zaman tamamen atlanmayan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="e278a-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="e278a-114"><xref:System.Uri.ToString%2A> bir kaçış karakterli '%', unescape değil '?', veya '#' karakteri.</span><span class="sxs-lookup"><span data-stu-id="e278a-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="e278a-115"><xref:System.Uri.Equals%2A> artık içerir <xref:System.Uri.Query%2A> eşitlik kontrolüne bölümün.</span><span class="sxs-lookup"><span data-stu-id="e278a-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="e278a-116">İşleçler "=="ve"! =" geçersiz kılındı ve bağlantılı <xref:System.Uri.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e278a-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="e278a-117"><xref:System.Uri.IsLoopback%2A> Şimdi tutarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="e278a-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="e278a-118">URI "`file:///path`" "file://path" artık çevrilir.</span><span class="sxs-lookup"><span data-stu-id="e278a-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="e278a-119">"#" şimdi bir ana bilgisayar adı Sonlandırıcı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e278a-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="e278a-120">Diğer bir deyişle, "http://consoto.com#fragment"şimdi dönüştürülür"http://contoso.com/#fragment".</span><span class="sxs-lookup"><span data-stu-id="e278a-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="e278a-121">Taban URI ile bir parça birleştirilirken hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="e278a-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="e278a-122">Bir hata <xref:System.Uri.HostNameType%2A> sabittir.</span><span class="sxs-lookup"><span data-stu-id="e278a-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="e278a-123">NNTP ayrıştırılırken bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="e278a-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="e278a-124">URI biçiminde HTTP:contoso.com şimdi bir ayrıştırma özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e278a-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="e278a-125">Framework doğru kullanıcı bilgisi bir URI olarak işler.</span><span class="sxs-lookup"><span data-stu-id="e278a-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="e278a-126">Kopuk bir URI Kökü yukarıda dosya sistemi çapraz geçiş yapamazsınız böylece URI yolu sıkıştırma düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e278a-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e278a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e278a-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
