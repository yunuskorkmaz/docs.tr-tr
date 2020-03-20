---
title: Sürüm 2.0'da System.Uri ad alanında yapılan değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642769"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="4fc17-102">Sürüm 2.0'da System.Uri ad alanında yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="4fc17-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="4fc17-103"><xref:System.Uri?displayProperty=nameWithType> Sınıfta çeşitli değişiklikler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="4fc17-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4fc17-104">Bu değişiklikler yanlış davranışı, gelişmiş kullanılabilirliği ve gelişmiş güvenliği düzelttirdi.</span><span class="sxs-lookup"><span data-stu-id="4fc17-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="4fc17-105">Eski ve yıkıntılı Üyeler</span><span class="sxs-lookup"><span data-stu-id="4fc17-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="4fc17-106">Kurucular:</span><span class="sxs-lookup"><span data-stu-id="4fc17-106">Constructors:</span></span>

- <span data-ttu-id="4fc17-107">`dontEscape` Parametresi olan tüm yapıcılar.</span><span class="sxs-lookup"><span data-stu-id="4fc17-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="4fc17-108">Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="4fc17-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="4fc17-109">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="4fc17-109">Changes</span></span>

- <span data-ttu-id="4fc17-110">Sorgu bölümü (dosya, ftp ve diğerleri) olmadığı bilinen URI düzenleri için '?' karakteri her zaman kaçar <xref:System.Uri.Query%2A> ve bir bölümün başlangıcı olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="4fc17-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="4fc17-111">Örtük dosya URI'leri `c:\directory\file@name.txt`(formdan), parça karakteri ('#') her zaman tam <xref:System.Uri.LocalPath%2A> `true`unescaping istenmedikçe veya .</span><span class="sxs-lookup"><span data-stu-id="4fc17-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="4fc17-112">UNC hostname desteği kaldırıldı; uluslararası ana bilgisayar adlarını temsil eden IDN belirtimi kabul edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="4fc17-113"><xref:System.Uri.LocalPath%2A>her zaman tamamen kaçılmamış bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fc17-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="4fc17-114"><xref:System.Uri.ToString%2A>kaçan bir '%', '?'veya '#' karakterinden kaçmaz.</span><span class="sxs-lookup"><span data-stu-id="4fc17-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="4fc17-115"><xref:System.Uri.Equals%2A>şimdi eşitlik <xref:System.Uri.Query%2A> denetimindeki bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="4fc17-116">"==" ve "!=" işleçleri geçersiz <xref:System.Uri.Equals%2A> kılınmış ve yönteme bağlanır.</span><span class="sxs-lookup"><span data-stu-id="4fc17-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="4fc17-117"><xref:System.Uri.IsLoopback%2A>şimdi tutarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="4fc17-118">URI "`file:///path`" artık `file://path`.</span><span class="sxs-lookup"><span data-stu-id="4fc17-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="4fc17-119">"#" artık bir ana bilgisayar adı sonlandırıcısı olarak kabul edilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="4fc17-120">Yani, `http://contoso.com#fragment` şimdi dönüştürülür `http://contoso.com/#fragment`.</span><span class="sxs-lookup"><span data-stu-id="4fc17-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="4fc17-121">Bir temel URI'yi bir parçayla birleştirirken bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="4fc17-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="4fc17-122">Bir hata <xref:System.Uri.HostNameType%2A> giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="4fc17-123">NNTP ayrıştırma bir hata giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="4fc17-124">Formun bir URI HTTP:contoso.com şimdi bir ayrıştırma özel atar.</span><span class="sxs-lookup"><span data-stu-id="4fc17-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="4fc17-125">Framework, bir URI'deki userinfo'yu doğru şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="4fc17-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="4fc17-126">URI yol sıkıştırma, bozuk bir URI'nin dosya sisteminde kökün üzerinde geçememesi için sabitlenir.</span><span class="sxs-lookup"><span data-stu-id="4fc17-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fc17-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fc17-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
