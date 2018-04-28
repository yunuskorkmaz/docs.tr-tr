---
title: Üyeler (F#)
description: 'Nesne üyeleri F # programlama dili hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a37f14d138cc017cf78e3a0ff1d5b5bba2f09020
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="members"></a><span data-ttu-id="603de-103">Üyeler</span><span class="sxs-lookup"><span data-stu-id="603de-103">Members</span></span>

<span data-ttu-id="603de-104">Bu bölümde, F # nesne türleri üyeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="603de-104">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="603de-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="603de-105">Remarks</span></span>
<span data-ttu-id="603de-106">*Üyeleri* türü tanımının bir parçası olan ve ile bildirilen özellikler `member` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="603de-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="603de-107">F # nesne türleri gibi kayıtları, sınıflar, birleşimler, arabirimleri ve üyeleri yapılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="603de-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="603de-108">Daha fazla bilgi için bkz: [kayıtları](../records.md), [sınıfları](../classes.md), [ayrılmış birleşimler](../discriminated-Unions.md), [arabirimleri](../interfaces.md), ve [yapıları](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="603de-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="603de-109">Üyeleri genellikle aksi belirtilmediği sürece ortak neden olan bir tür için ortak arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="603de-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="603de-110">Üyeleri, özel veya dahili bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="603de-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="603de-111">Daha fazla bilgi için bkz: [erişim denetimi](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="603de-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="603de-112">İmzaları türleri için kullanıma sunmak veya belirli bir türün üyeleri kullanıma sunmak değil de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="603de-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="603de-113">Daha fazla bilgi için bkz: [imzalar](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="603de-113">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="603de-114">Özel alanlar ve `do` yalnızca sınıflarıyla kullanılan bağlamaları olmayan true üyeleri, çünkü bunlar hiçbir zaman bir türde ortak arabirimi parçası olan ve ile bildirilmemiş `member` anahtar sözcüğü, ancak bunlar açıklanmıştır Bu bölümde ayrıca.</span><span class="sxs-lookup"><span data-stu-id="603de-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="603de-115">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="603de-115">Related Topics</span></span>


|<span data-ttu-id="603de-116">Konu</span><span class="sxs-lookup"><span data-stu-id="603de-116">Topic</span></span>|<span data-ttu-id="603de-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="603de-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="603de-118">`let` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="603de-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="603de-119">Özel alanları ve sınıfları işlevleri tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="603de-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="603de-120">`do` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="603de-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="603de-121">Nesne başlatma kodu belirtimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="603de-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="603de-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="603de-122">Properties</span></span>](properties.md)|<span data-ttu-id="603de-123">Özellik üyelerinde sınıfları ve diğer türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="603de-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="603de-124">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="603de-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="603de-125">Dizi benzeri özelliklerinde sınıfları ve diğer türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="603de-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="603de-126">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="603de-126">Methods</span></span>](methods.md)|<span data-ttu-id="603de-127">Bir tür üyesi işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="603de-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="603de-128">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="603de-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="603de-129">Bir türdeki nesneleri başlatma özel işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="603de-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="603de-130">İşleç Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="603de-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="603de-131">Türleri için özelleştirilmiş işleçleri tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="603de-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="603de-132">Olaylar</span><span class="sxs-lookup"><span data-stu-id="603de-132">Events</span></span>](events.md)|<span data-ttu-id="603de-133">Olayların ve olay işleme desteği F # tanımı açıklar.</span><span class="sxs-lookup"><span data-stu-id="603de-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="603de-134">Belirtik Alanlar: `val` Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="603de-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="603de-135">Bir türdeki başlatılmamış alanları tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="603de-135">Describes the definition of uninitialized fields in a type.</span></span>|
