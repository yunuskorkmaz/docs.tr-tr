---
title: Üyeler (F#)
description: 'Nesne üyeleri F # programlama dili hakkında bilgi edinin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="8df91-104">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8df91-104">Members</span></span>

<span data-ttu-id="8df91-105">Bu bölümde, F # nesne türleri üyeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8df91-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="8df91-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8df91-106">Remarks</span></span>
<span data-ttu-id="8df91-107">*Üyeleri* türü tanımının bir parçası olan ve ile bildirilen özellikler `member` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8df91-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="8df91-108">F # nesne türleri gibi kayıtları, sınıflar, birleşimler, arabirimleri ve üyeleri yapılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="8df91-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="8df91-109">Daha fazla bilgi için bkz: [kayıtları](../records.md), [sınıfları](../classes.md), [ayrılmış birleşimler](../discriminated-Unions.md), [arabirimleri](../interfaces.md), ve [yapıları](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="8df91-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="8df91-110">Üyeleri genellikle aksi belirtilmediği sürece ortak neden olan bir tür için ortak arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8df91-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="8df91-111">Üyeleri, özel veya dahili bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8df91-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="8df91-112">Daha fazla bilgi için bkz: [erişim denetimi](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="8df91-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="8df91-113">İmzaları türleri için kullanıma sunmak veya belirli bir türün üyeleri kullanıma sunmak değil de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8df91-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="8df91-114">Daha fazla bilgi için bkz: [imzalar](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="8df91-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="8df91-115">Özel alanlar ve `do` yalnızca sınıflarıyla kullanılan bağlamaları olmayan true üyeleri, çünkü bunlar hiçbir zaman bir türde ortak arabirimi parçası olan ve ile bildirilmemiş `member` anahtar sözcüğü, ancak bunlar açıklanmıştır Bu bölümde ayrıca.</span><span class="sxs-lookup"><span data-stu-id="8df91-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="8df91-116">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="8df91-116">Related Topics</span></span>


|<span data-ttu-id="8df91-117">Konu</span><span class="sxs-lookup"><span data-stu-id="8df91-117">Topic</span></span>|<span data-ttu-id="8df91-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8df91-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="8df91-119">`let`Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="8df91-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="8df91-120">Özel alanları ve sınıfları işlevleri tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8df91-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="8df91-121">`do`Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="8df91-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="8df91-122">Nesne başlatma kodu belirtimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8df91-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="8df91-123">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8df91-123">Properties</span></span>](properties.md)|<span data-ttu-id="8df91-124">Özellik üyelerinde sınıfları ve diğer türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8df91-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="8df91-125">Dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="8df91-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="8df91-126">Dizi benzeri özelliklerinde sınıfları ve diğer türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8df91-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="8df91-127">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="8df91-127">Methods</span></span>](methods.md)|<span data-ttu-id="8df91-128">Bir tür üyesi işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8df91-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="8df91-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8df91-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="8df91-130">Bir türdeki nesneleri başlatma özel işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8df91-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="8df91-131">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="8df91-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="8df91-132">Türleri için özelleştirilmiş işleçleri tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8df91-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="8df91-133">Olayları</span><span class="sxs-lookup"><span data-stu-id="8df91-133">Events</span></span>](events.md)|<span data-ttu-id="8df91-134">Olayların ve olay işleme desteği F # tanımı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8df91-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="8df91-135">Açık alanlar: `val` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="8df91-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="8df91-136">Bir türdeki başlatılmamış alanları tanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8df91-136">Describes the definition of uninitialized fields in a type.</span></span>|
