---
description: 'Daha fazla bilgi edinin: alan tasarımı'
title: Alan Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 88df60c3050035221dc65429bbd543c71d5d69b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642051"
---
# <a name="field-design"></a><span data-ttu-id="dfb4e-103">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="dfb4e-103">Field Design</span></span>

<span data-ttu-id="dfb4e-104">Kapsülleme prensibi, nesne odaklı tasarımda en önemli olmaların biridir.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-104">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="dfb4e-105">Bu ilke, bir nesne içinde depolanan verilerin yalnızca o nesnenin erişimine açık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-105">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="dfb4e-106">Prensibi yorumlamak için kullanışlı bir yol, türün (ad veya tür değişiklikleri) alanlara yapılan değişikliklerin, türün üyeleri için dışında bir kod olmadan yapılabilmesi için bir türün tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-106">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="dfb4e-107">Bu yorum hemen tüm alanların özel olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-107">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="dfb4e-108">Bu katı kısıtlamadan yalnızca sabit ve statik salt okunurdur alanları hariç tutduk, çünkü bu tür alanlar, neredeyse tanım için hiçbir şekilde değişiklik gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-108">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="dfb4e-109">❌ Ortak veya korumalı örnek alanlarını sağlamaın.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-109">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="dfb4e-110">Genel veya korumalı hale getirmek yerine alanlara erişim için özellikler sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-110">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="dfb4e-111">✔️ hiçbir şekilde değişmeyecek sabitler için sabit alanlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-111">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="dfb4e-112">Derleyici const alanlarının değerlerini doğrudan çağıran koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-112">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="dfb4e-113">Bu nedenle, sabit değerler hiçbir şekilde uyumluluk riski olmadan değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-113">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="dfb4e-114">✔️ `readonly` önceden tanımlanmış nesne örnekleri için ortak statik alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-114">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="dfb4e-115">Türün önceden tanımlanmış örnekleri varsa, bunları türün kendisine ait public salt okunurdur statik alanlar olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-115">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="dfb4e-116">❌ Alanlara kesilebilir türlerin örneklerini atamayın `readonly` .</span><span class="sxs-lookup"><span data-stu-id="dfb4e-116">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="dfb4e-117">Kesilebilir tür, örneklendirildikten sonra değiştirilebilen örneklere sahip bir türdür.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-117">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="dfb4e-118">Örneğin, diziler, en çok koleksiyonlar ve akışlar değişebilir türlerdir, ancak, <xref:System.Int32?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> ve <xref:System.String?displayProperty=nameWithType> sabittir.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-118">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="dfb4e-119">Bir başvuru türü alanındaki salt okunurdur değiştirici, alanda depolanan örneğin değiştirilmesini önler, ancak örneği değiştiren Üyeler çağırarak alanın örnek verilerinin değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-119">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="dfb4e-120">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="dfb4e-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dfb4e-121">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="dfb4e-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dfb4e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb4e-122">See also</span></span>

- [<span data-ttu-id="dfb4e-123">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dfb4e-123">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="dfb4e-124">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dfb4e-124">Framework Design Guidelines</span></span>](index.md)
