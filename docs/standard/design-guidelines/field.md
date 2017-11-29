---
title: "Alan tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dc3249518dd1e1c751de08c22d1c5eb4fa28dc6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="field-design"></a><span data-ttu-id="8914b-102">Alan tasarım</span><span class="sxs-lookup"><span data-stu-id="8914b-102">Field Design</span></span>
<span data-ttu-id="8914b-103">Saklama ilkesini en önemli kavramları nesne odaklı tasarım biridir.</span><span class="sxs-lookup"><span data-stu-id="8914b-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="8914b-104">Bu ilke, bir nesne içinde depolanan veriler yalnızca o nesneyi erişilebilir olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8914b-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="8914b-105">Böylece türü üyeleri için kod dışında bozmadan alanları türü (adı veya türü değişiklikleri) yapılan değişiklikler yapılabilir bir türü tasarlanmalıdır söylemek için ilkesini yorumlamak için kullanışlı bir yol olduğu.</span><span class="sxs-lookup"><span data-stu-id="8914b-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="8914b-106">Bu yorum hemen tüm alanları özel anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8914b-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="8914b-107">Bu tür alanları neredeyse tanımı tarafından hiçbir zaman değiştirmek için gerekli olduğundan Biz bu katı sınırlama listesinden sabit ve statik salt okunur alanları hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="8914b-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="8914b-108">**X yok** genel veya korumalı örneği alanları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8914b-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="8914b-109">Genel veya korumalı yapmak yerine alanları erişmek için özellikler sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8914b-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="8914b-110">**✓ YAPMAK** için hiçbir zaman değiştirecek sabitleri sabit alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="8914b-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="8914b-111">Derleyici, doğrudan kod çağırma içine const alanlarına ait değerlerin yakar.</span><span class="sxs-lookup"><span data-stu-id="8914b-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="8914b-112">Bu nedenle, sabit değerler hiçbir zaman uyumluluk çiğnemekten riski değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8914b-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="8914b-113">**✓ YAPMAK** ortak statik kullanmak `readonly` alanları önceden tanımlanmış nesne örnekleri için.</span><span class="sxs-lookup"><span data-stu-id="8914b-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="8914b-114">Önceden tanımlanmış türünün örneklerini varsa, bunları genel olarak salt okunur statik alanları türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="8914b-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="8914b-115">**X yok** değişebilir türlerin örnekleri atamak `readonly` alanları.</span><span class="sxs-lookup"><span data-stu-id="8914b-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="8914b-116">Bir örneği sonra değiştirilebilen örnekleri türüyle bir değişebilir türüdür.</span><span class="sxs-lookup"><span data-stu-id="8914b-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="8914b-117">Örneğin, dizileri, birçok koleksiyonun ve akışlar değişebilir türleridir ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, ve <xref:System.String?displayProperty=nameWithType> tüm sabittir.</span><span class="sxs-lookup"><span data-stu-id="8914b-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="8914b-118">Bir başvuru türü alanı üzerinde salt okunur değiştiricisi değiştirilmekte olan gelen alanda depolanan örneği engeller, ancak alanın örnek veri örneğini değiştirme arama üyeleri tarafından değiştirilmiş engellemez.</span><span class="sxs-lookup"><span data-stu-id="8914b-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="8914b-119">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8914b-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8914b-120">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="8914b-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8914b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8914b-121">See Also</span></span>  
 [<span data-ttu-id="8914b-122">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8914b-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="8914b-123">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8914b-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
