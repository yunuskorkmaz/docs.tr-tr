---
title: "Yerel sistemde tanımlanan saat dilimlerini bulma"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="d4139-102">Yerel sistemde tanımlanan saat dilimlerini bulma</span><span class="sxs-lookup"><span data-stu-id="d4139-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="d4139-103"><xref:System.TimeZoneInfo> Sınıfı bir public oluşturucuya uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="d4139-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="d4139-104">Sonuç olarak, `new` anahtar sözcüğü, yeni bir oluşturmak için kullanılamaz <xref:System.TimeZoneInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d4139-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="d4139-105">Bunun yerine, <xref:System.TimeZoneInfo> nesnelerine ait örneklerin kayıt defterinden önceden tanımlanmış saat dilimleri hakkında bilgi almak veya özel bir saat dilimi oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="d4139-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="d4139-106">Bu konuda, bir saat dilimi kayıt defterinde depolanan verilerden başlatmasını anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4139-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="d4139-107">Ayrıca, `static` (`shared` Visual Basic'te) özelliklerini <xref:System.TimeZoneInfo> sınıfı Eşgüdümlü Evrensel Saat (UTC) ve yerel saat dilimini erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4139-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="d4139-108">Kayıt defterinde tanımlı değil saat dilimleri için özel saat dilimlerini aşırı çağırarak oluşturabileceğiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4139-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="d4139-109">Özel bir saat dilimi oluşturma ele alınmıştır [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="d4139-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="d4139-110">Ayrıca, örneği bir <xref:System.TimeZoneInfo> ile seri hale getirilmiş bir dizeden geri nesne <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4139-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="d4139-111">Seri hale getirme ve seri durumdan çıkarılırken bir <xref:System.TimeZoneInfo> nesne ele alınmıştır [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="d4139-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="d4139-112">Tek tek saat dilimleri erişme</span><span class="sxs-lookup"><span data-stu-id="d4139-112">Accessing individual time zones</span></span>

<span data-ttu-id="d4139-113"><xref:System.TimeZoneInfo> Sınıfı UTC saati ve yerel saat dilimini temsil eden iki önceden tanımlanmış saat dilimi nesneleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4139-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="d4139-114">Kullanılabilir <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A> özellikleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d4139-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="d4139-115">UTC veya yerel saat dilimlerini erişme ile ilgili yönergeler için bkz: [nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="d4139-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="d4139-116">Ayrıca örneği bir <xref:System.TimeZoneInfo> kayıt defterinde tanımlanan tüm saat dilimini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d4139-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="d4139-117">Belirli saat dilimi nesnesi örneği ile ilgili yönergeler için bkz: [nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="d4139-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="d4139-118">Saat dilimi tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="d4139-118">Time zone identifiers</span></span>

<span data-ttu-id="d4139-119">Saat dilimi benzersiz olarak tanımlayan bir anahtar alanı saat dilimi tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="d4139-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="d4139-120">Çoğu anahtarları görece kısa olsa da, saat dilimi tanımlayıcı daha uzun.</span><span class="sxs-lookup"><span data-stu-id="d4139-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="d4139-121">Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> saat diliminin standart saat adını sağlamak için kullanılan özellik.</span><span class="sxs-lookup"><span data-stu-id="d4139-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="d4139-122">Ancak, özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="d4139-122">However, there are exceptions.</span></span> <span data-ttu-id="d4139-123">Geçerli bir tanımlayıcı sağladığınız emin olmak için en iyi sisteminizdeki kullanılabilir saat dilimlerini numaralandırma ve bunların ilişkili tanımlayıcıları not edin yoludur.</span><span class="sxs-lookup"><span data-stu-id="d4139-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4139-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4139-124">See also</span></span>

<span data-ttu-id="d4139-125">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md)
[nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="d4139-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
