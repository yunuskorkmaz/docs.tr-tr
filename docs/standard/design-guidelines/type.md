---
title: Türü tasarım yönergeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 53c7bccd4afb92e6afcaccf4b1c50c41f574fedb
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="type-design-guidelines"></a><span data-ttu-id="eda96-102">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="eda96-102">Type Design Guidelines</span></span>
<span data-ttu-id="eda96-103">CLR açısından türleri yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri — ancak framework tasarımı ile ilgili bir tartışma amacıyla biz türleri her kendi özel tasarım kurallarla daha fazla mantıksal gruplar halinde bölün.</span><span class="sxs-lookup"><span data-stu-id="eda96-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="eda96-104">Başvuru türleri genel durumunun sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="eda96-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="eda96-105">Bunlar çerçeveleri çoğunluğu türlerinde toplu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eda96-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="eda96-106">Sınıfları, destekledikleri nesne yönelimli özelliklerini ayarla zengin ve genel uygulanabilirlikleri kendi popülerliği borçlu olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="eda96-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="eda96-107">Temel sınıflar ve soyut sınıflar için genişletilebilirlik ilgili özel mantıksal gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="eda96-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="eda96-108">Arabirimleri uygulanabilecek başvuru türleri ve değer türleri tarafından türleridir.</span><span class="sxs-lookup"><span data-stu-id="eda96-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="eda96-109">Bu nedenle başvuru türleri ve değer türlerini biçimli hiyerarşileri kökleri hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="eda96-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="eda96-110">Ayrıca, arabirimleri CLR tarafından yerel olarak desteklenmeyen birden çok devralma benzetimini yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eda96-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="eda96-111">Yapılar genel durumda değer türlerini ve küçük, basit türleri, dil temelleri benzer için ayrılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eda96-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="eda96-112">Numaralandırmalar bir özel durum gün haftanın günü, konsol renkleri ve benzerleri gibi değerler kısa kümesini tanımlamak için kullanılan değer türlerini ' dir.</span><span class="sxs-lookup"><span data-stu-id="eda96-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="eda96-113">Statik sınıflar statik üyeler için kapsayıcı olarak kullanılması türleridir.</span><span class="sxs-lookup"><span data-stu-id="eda96-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="eda96-114">Diğer işlemlerin kısayollar sağlamak için yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eda96-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="eda96-115">Temsilciler, özel durumlar, öznitelikler, dizileri ve koleksiyonları referans tür belirli kullanımlar için hedeflenen tüm özel durumlar ve tasarım ve kullanım yönergeleri başka bir yerde bu kitap ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="eda96-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="eda96-116">**✓ YAPMAK** her tür iyi tanımlanmış bir grup yalnızca rastgele koleksiyonunu ilgisiz işlevselliği ilgili üyesi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eda96-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eda96-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eda96-117">In This Section</span></span>  
 [<span data-ttu-id="eda96-118">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="eda96-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="eda96-119">Soyut Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="eda96-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="eda96-120">Statik Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="eda96-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="eda96-121">Arabirim Tasarımı</span><span class="sxs-lookup"><span data-stu-id="eda96-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="eda96-122">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="eda96-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="eda96-123">Sabit Listesi Tasarımı</span><span class="sxs-lookup"><span data-stu-id="eda96-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="eda96-124">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="eda96-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="eda96-125">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="eda96-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="eda96-126">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="eda96-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda96-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eda96-127">See Also</span></span>  
 [<span data-ttu-id="eda96-128">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="eda96-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
