---
title: "Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="e44ea-102">Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e44ea-102">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="e44ea-103">Örneği oluşturmak için en yaygın yolu bir <xref:System.TimeZoneInfo> nesnesidir ilgili bilgileri kayıt defterinden alınamadı.</span><span class="sxs-lookup"><span data-stu-id="e44ea-103">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="e44ea-104">Bu konuda ele alınmıştır örneği oluşturmak nasıl bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-104">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="e44ea-105">Timezoneınfo nesnesinin örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e44ea-105">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="e44ea-106">Bildirme bir <xref:System.TimeZoneInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-106">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="e44ea-107">Çağrı `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-107">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="e44ea-108">Yöntemi tarafından oluşturulan tüm özel durumları işleme özellikle <xref:System.TimeZoneNotFoundException> saat dilimi kayıt defterinde tanımlanmazsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="e44ea-108">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="e44ea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e44ea-109">Example</span></span>

<span data-ttu-id="e44ea-110">Aşağıdaki kod alır bir <xref:System.TimeZoneInfo> Doğu Standart saat dilimi temsil eder ve karşılık gelen Doğu Standart Saati yerel saate görüntüleyen nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-110">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="e44ea-111"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Yöntemin tek bir parametre, saat almak istediğiniz nesnenin karşılık gelen dilimi tanımlayıcısıdır <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e44ea-111">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e44ea-112">Saat dilimi benzersiz olarak tanımlayan bir anahtar alanı saat dilimi tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e44ea-112">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="e44ea-113">Çoğu anahtarları görece kısa olsa da, saat dilimi tanımlayıcı daha uzun.</span><span class="sxs-lookup"><span data-stu-id="e44ea-113">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="e44ea-114">Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A> özelliği bir <xref:System.TimeZoneInfo> saat diliminin standart saat adını sağlamak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="e44ea-114">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="e44ea-115">Ancak, özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="e44ea-115">However, there are exceptions.</span></span> <span data-ttu-id="e44ea-116">Geçerli bir tanımlayıcı sağladığınız emin olmak için en iyi sisteminizdeki kullanılabilir saat dilimlerini numaralandırma ve bunlar üzerinde mevcut saat dilimlerini tanımlayıcıların not edin yoludur.</span><span class="sxs-lookup"><span data-stu-id="e44ea-116">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="e44ea-117">Çizim için bkz: [nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="e44ea-117">For an illustration, see [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span></span> <span data-ttu-id="e44ea-118">[Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) konu, seçili saat dilimi tanımlayıcıları listesini de içerir.</span><span class="sxs-lookup"><span data-stu-id="e44ea-118">The [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="e44ea-119">Saat dilimi bulunursa, yöntem, <xref:System.TimeZoneInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-119">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="e44ea-120">Saat dilimi bulunamazsa, yöntem oluşturulur bir <xref:System.TimeZoneNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="e44ea-120">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="e44ea-121">Saat dilimi bulundu, ancak verileri bozuk veya eksik yöntemi atar bir <xref:System.InvalidTimeZoneException>.</span><span class="sxs-lookup"><span data-stu-id="e44ea-121">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="e44ea-122">Uygulamanızı mevcut bir saat dilimini temel dayalıysa, ilk çağırmalısınız <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> kayıt defterinden saat dilimi bilgilerini alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-122">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="e44ea-123">Yöntem çağrısının başarısız olursa, özel durum işleyici sonra saat dilimi yeni bir örneğini oluşturmak veya seri hale getirilmiş bir seri durumdan tarafından yeniden oluşturun <xref:System.TimeZoneInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e44ea-123">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="e44ea-124">Bkz: [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) bir örnek.</span><span class="sxs-lookup"><span data-stu-id="e44ea-124">See [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="e44ea-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e44ea-125">See also</span></span>

<span data-ttu-id="e44ea-126">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md)</span><span class="sxs-lookup"><span data-stu-id="e44ea-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)</span></span>
