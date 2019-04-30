---
title: Tür Tasarımı Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650108"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="e42c0-102">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e42c0-102">Type Design Guidelines</span></span>
<span data-ttu-id="e42c0-103">CLR açısından bakıldığında, türlerin yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri — ancak çerçevesi tasarımı hakkında bir tartışma amacıyla biz türleri her biri kendi belirli tasarım kuralları ile daha fazla mantıksal gruplar halinde bölün.</span><span class="sxs-lookup"><span data-stu-id="e42c0-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="e42c0-104">Başvuru türlerinin genel durum sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="e42c0-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="e42c0-105">Bunlar toplu çerçeveleri çoğunu türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e42c0-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="e42c0-106">Sınıflar nesne yönelimli özellikleri destekledikleri zengin ve genel uygulanabilirlikleri, popülerliğini borçlu.</span><span class="sxs-lookup"><span data-stu-id="e42c0-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="e42c0-107">Temel sınıflar ve soyut sınıflar için genişletilebilirlik ilgili özel mantıksal gruplardır.</span><span class="sxs-lookup"><span data-stu-id="e42c0-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="e42c0-108">Başvuru türleri ve değer türleri tarafından uygulanabilir türleri arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="e42c0-109">Bu nedenle çok biçimli Hiyerarşiler başvuru türleri ve değer türlerinin kökleri hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="e42c0-110">Ayrıca, arabirimler CLR tarafından yerel olarak desteklenmeyen birden çok devralma benzetimini yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="e42c0-111">Yapılar değer türlerinin genel büyük ve küçük, basit türler, benzer dil temelleri için ayrılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="e42c0-112">Numaralandırmalar bir özel durum değerlerinin gün haftanın günü, konsol renkleri ve benzeri gibi kısa kümesi tanımlamak için kullanılan değer türlerinin ' dir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="e42c0-113">Statik sınıflar statik üyeleri için kapsayıcılar olmasını türleridir.</span><span class="sxs-lookup"><span data-stu-id="e42c0-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="e42c0-114">Diğer işlemler için kısayollar sağlamak için yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e42c0-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="e42c0-115">Başvuru türlerinin belirli kullanımlar için hedeflenen tüm özel durumlar Temsilciler, özel durumlar, öznitelikler, diziler ve koleksiyonlar olan ve onların tasarım ve kullanım için yönergeler bu kitap başka bir yerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="e42c0-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="e42c0-116">**✓ DO** her tür iyi tanımlanmış bir grup yalnızca rastgele koleksiyonunu ilgisiz işlevselliği ilgili üyesi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e42c0-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e42c0-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e42c0-117">In This Section</span></span>  
 [<span data-ttu-id="e42c0-118">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="e42c0-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="e42c0-119">Soyut Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e42c0-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="e42c0-120">Statik Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e42c0-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="e42c0-121">Arabirim Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e42c0-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="e42c0-122">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e42c0-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="e42c0-123">Sabit Listesi Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e42c0-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="e42c0-124">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="e42c0-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="e42c0-125">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e42c0-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e42c0-126">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="e42c0-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42c0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e42c0-127">See also</span></span>

- [<span data-ttu-id="e42c0-128">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e42c0-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
