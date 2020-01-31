---
title: Alan Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: c00929ca499e39bd4e24d482c9413beb9cccddc1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741603"
---
# <a name="field-design"></a><span data-ttu-id="de253-102">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="de253-102">Field Design</span></span>
<span data-ttu-id="de253-103">Kapsülleme prensibi, nesne odaklı tasarımda en önemli olmaların biridir.</span><span class="sxs-lookup"><span data-stu-id="de253-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="de253-104">Bu ilke, bir nesne içinde depolanan verilerin yalnızca o nesnenin erişimine açık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de253-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="de253-105">Prensibi yorumlamak için kullanışlı bir yol, türün (ad veya tür değişiklikleri) alanlara yapılan değişikliklerin, türün üyeleri için dışında bir kod olmadan yapılabilmesi için bir türün tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de253-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="de253-106">Bu yorum hemen tüm alanların özel olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="de253-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="de253-107">Bu katı kısıtlamadan yalnızca sabit ve statik salt okunurdur alanları hariç tutduk, çünkü bu tür alanlar, neredeyse tanım için hiçbir şekilde değişiklik gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="de253-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="de253-108">❌ ortak veya korumalı örnek alanlar sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="de253-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="de253-109">Genel veya korumalı hale getirmek yerine alanlara erişim için özellikler sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="de253-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="de253-110">✔️ hiçbir şekilde değişmeyecek sabitler için sabit alanlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="de253-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="de253-111">Derleyici const alanlarının değerlerini doğrudan çağıran koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="de253-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="de253-112">Bu nedenle, sabit değerler hiçbir şekilde uyumluluk riski olmadan değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="de253-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="de253-113">✔️ önceden tanımlanmış nesne örnekleri için ortak statik `readonly` alanlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="de253-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="de253-114">Türün önceden tanımlanmış örnekleri varsa, bunları türün kendisine ait public salt okunurdur statik alanlar olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="de253-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="de253-115">❌, `readonly` alanlara kesilebilir türlerin örneklerini atamayın.</span><span class="sxs-lookup"><span data-stu-id="de253-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="de253-116">Kesilebilir tür, örneklendirildikten sonra değiştirilebilen örneklere sahip bir türdür.</span><span class="sxs-lookup"><span data-stu-id="de253-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="de253-117">Örneğin, diziler, en çok koleksiyonlar ve akışlar değişebilir türlerdir, ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>ve <xref:System.String?displayProperty=nameWithType> sabittir.</span><span class="sxs-lookup"><span data-stu-id="de253-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="de253-118">Bir başvuru türü alanındaki salt okunurdur değiştirici, alanda depolanan örneğin değiştirilmesini önler, ancak örneği değiştiren Üyeler çağırarak alanın örnek verilerinin değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="de253-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="de253-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="de253-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="de253-120">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="de253-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="de253-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de253-121">See also</span></span>

- [<span data-ttu-id="de253-122">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="de253-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="de253-123">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="de253-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
