---
description: "Hakkında daha fazla bilgi edinin: sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler"
title: Sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 8b5e2f2b3b59fba96e20e40a4df18273a2f6034f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791627"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="6b84e-103">Sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler</span><span class="sxs-lookup"><span data-stu-id="6b84e-103">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="6b84e-104">Sınıfta birkaç değişiklik yapılmıştır <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6b84e-104">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6b84e-105">Bu değişiklikler hatalı davranışı, gelişmiş kullanılabilirliği ve geliştirilmiş güvenliği düzelttik.</span><span class="sxs-lookup"><span data-stu-id="6b84e-105">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="6b84e-106">Kullanımdan kaldırılan ve kullanım dışı bırakılmış Üyeler</span><span class="sxs-lookup"><span data-stu-id="6b84e-106">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="6b84e-107">Kurucu</span><span class="sxs-lookup"><span data-stu-id="6b84e-107">Constructors:</span></span>

- <span data-ttu-id="6b84e-108">Parametresi olan tüm oluşturucular `dontEscape` .</span><span class="sxs-lookup"><span data-stu-id="6b84e-108">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="6b84e-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6b84e-109">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="6b84e-110">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="6b84e-110">Changes</span></span>

- <span data-ttu-id="6b84e-111">Bir sorgu bölümüne (dosya, FTP ve diğerleri) sahip olmadığı bilinen URI şemaları için, '? ' karakteri her zaman kaçışın ve bir parçanın başlangıcını kabul etmez <xref:System.Uri.Query%2A> .</span><span class="sxs-lookup"><span data-stu-id="6b84e-111">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="6b84e-112">Örtük dosya URI 'Leri (form) için `c:\directory\file@name.txt` , tam kaçış istenmediği veya olduğu müddetçe, parça karakteri (' # ') her zaman atlanmalıdır <xref:System.Uri.LocalPath%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="6b84e-112">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="6b84e-113">UNC konak adı desteği kaldırıldı; Uluslararası ana bilgisayar adlarını temsil eden ıDN belirtimi benimsendi.</span><span class="sxs-lookup"><span data-stu-id="6b84e-113">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="6b84e-114"><xref:System.Uri.LocalPath%2A> her zaman tamamen kaçışsız bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b84e-114"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="6b84e-115"><xref:System.Uri.ToString%2A> kaçışın '% ', '? ' veya ' # ' karakterinin kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6b84e-115"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="6b84e-116"><xref:System.Uri.Equals%2A> Artık <xref:System.Uri.Query%2A> eşitlik denetiminin bölümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="6b84e-116"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="6b84e-117">"= =" Ve "! =" işleçleri geçersiz kılınır ve <xref:System.Uri.Equals%2A> yöntemine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="6b84e-117">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="6b84e-118"><xref:System.Uri.IsLoopback%2A> Artık tutarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="6b84e-118"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="6b84e-119">"" URI 'SI `file:///path` artık öğesine çevrilmedi `file://path` .</span><span class="sxs-lookup"><span data-stu-id="6b84e-119">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="6b84e-120">"#" artık ana bilgisayar adı Sonlandırıcı olarak tanınıyor.</span><span class="sxs-lookup"><span data-stu-id="6b84e-120">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="6b84e-121">Diğer bir deyişle, `http://contoso.com#fragment` Şimdi öğesine dönüştürülür `http://contoso.com/#fragment` .</span><span class="sxs-lookup"><span data-stu-id="6b84e-121">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="6b84e-122">Temel URI 'yi bir parçaya birleştirilirken bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="6b84e-122">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="6b84e-123">İçindeki bir hata <xref:System.Uri.HostNameType%2A> düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="6b84e-123">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="6b84e-124">NNTP ayrıştırmasındaki bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="6b84e-124">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="6b84e-125">HTTP:contoso. com biçiminde bir URI artık ayrıştırma özel durumu oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="6b84e-125">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="6b84e-126">Framework bir URI 'de UserInfo doğru şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="6b84e-126">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="6b84e-127">URI yolu sıkıştırması, bozuk bir URI 'nin kök üzerindeki dosya sisteminde geçiş yapmasını sağlamak için düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="6b84e-127">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b84e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b84e-128">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
