---
title: Alan tasarımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65c54fe9a076a219c61280a98c390b16f56b5015
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252005"
---
# <a name="field-design"></a><span data-ttu-id="276f8-102">Alan tasarımı</span><span class="sxs-lookup"><span data-stu-id="276f8-102">Field Design</span></span>
<span data-ttu-id="276f8-103">Kapsülleme, en önemli kavramları nesne yönelimli tasarım biridir.</span><span class="sxs-lookup"><span data-stu-id="276f8-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="276f8-104">Bu ilke, nesnenin içinde depolanan veriler yalnızca o nesneye erişilebilir olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="276f8-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="276f8-105">İlke yorumlamak için kullanışlı bir yol, bir türü türün üyeleri için dışındaki kod bozmadan alanlar (ada veya türe değişiklikler) bu tür değişiklikler yapılabilir olacak şekilde tasarlanmalıdır söyleyin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="276f8-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="276f8-106">Bu yorumu, hemen tüm alanlar özel olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="276f8-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="276f8-107">Bu tür alanlar neredeyse tanımı gereği hiçbir zaman değiştirmek için gerekli olduğundan bu katı kısıtlaması, sabit ve statik salt okunur alanları tutarız.</span><span class="sxs-lookup"><span data-stu-id="276f8-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="276f8-108">**X DO NOT** genel veya korumalı örneği alanları sağlar.</span><span class="sxs-lookup"><span data-stu-id="276f8-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="276f8-109">Ortak veya korumalı yapmak yerine alanları erişmek için özellikler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="276f8-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="276f8-110">**✓ DO** için hiçbir zaman değiştirecek sabitleri sabit alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="276f8-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="276f8-111">Derleyici kod doğrudan çağırma içine const alanların değerlerini harekete.</span><span class="sxs-lookup"><span data-stu-id="276f8-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="276f8-112">Bu nedenle, sabit değerler hiçbir zaman uyumluluk bozucu riski değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="276f8-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="276f8-113">**✓ DO** ortak statik kullanmak `readonly` alanları önceden tanımlanmış nesne örnekleri için.</span><span class="sxs-lookup"><span data-stu-id="276f8-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="276f8-114">Önceden tanımlanmış tür örnekleri varsa, bunları genel olarak salt okunur statik alanları türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="276f8-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="276f8-115">**X DO NOT** değişebilir türlerin örnekleri atamak `readonly` alanları.</span><span class="sxs-lookup"><span data-stu-id="276f8-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="276f8-116">Kesilebilir tür örneklerle örneği oluşturulur sonra değiştirilebilen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="276f8-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="276f8-117">Örneğin, diziler, çoğu koleksiyonları ve akışları değişebilir türleridir ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, ve <xref:System.String?displayProperty=nameWithType> tüm sabittir.</span><span class="sxs-lookup"><span data-stu-id="276f8-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="276f8-118">Bir başvuru türü alanı salt okunur değiştiricisi değiştirilmesini alanında depolanan örneği engeller ancak alanın örnek verisinin örneğini değiştirme çağıran üyeleri tarafından değiştirilmesini önlemez.</span><span class="sxs-lookup"><span data-stu-id="276f8-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="276f8-119">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="276f8-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="276f8-120">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="276f8-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276f8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="276f8-121">See also</span></span>

- [<span data-ttu-id="276f8-122">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="276f8-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="276f8-123">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="276f8-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
