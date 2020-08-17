---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızdaki yeni dil özelliklerine giriş, onu kullanan kodu etkileyebilir.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: f7db7c79792d04bcf592bc1858e1f0f05cb34402
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268133"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="019c2-103">C# geliştiricileri için sürüm ve güncelleştirme konuları</span><span class="sxs-lookup"><span data-stu-id="019c2-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="019c2-104">Yeni özellikler C# diline eklendikçe uyumluluk çok önemli bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="019c2-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="019c2-105">Neredeyse tüm durumlarda, mevcut kod herhangi bir sorun olmadan yeni bir derleyici sürümü ile yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="019c2-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="019c2-106">Yeni dil özelliklerini bir kitaplıkta benimsediğinizde daha dikkatli olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="019c2-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="019c2-107">En son sürümde bulunan özelliklerle yeni bir kitaplık oluşturabilir ve derleyicinin önceki sürümlerini kullanarak oluşturulan uygulamaların bunu kullanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="019c2-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="019c2-108">Ya da var olan bir kitaplığı yükseltiyor olabilirsiniz ve kullanıcılarınızın birçoğu henüz yükseltilmiş sürüme sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="019c2-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="019c2-109">Yeni özellikleri benimseme konusunda kararlar verirken, iki uyumluluk çeşitlemelerini göz önünde bulundurmanız gerekir: kaynak ile uyumlu ve ikili uyumlu.</span><span class="sxs-lookup"><span data-stu-id="019c2-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="019c2-110">İkili uyumlu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="019c2-110">Binary compatible changes</span></span>

<span data-ttu-id="019c2-111">Güncelleştirilmiş kitaplığınız, onu kullanan uygulamaları ve kitaplıkları yeniden oluşturmadan kullanılabilir olduğunda, kitaplığınızdaki değişiklikler **ikili uyumludur** .</span><span class="sxs-lookup"><span data-stu-id="019c2-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="019c2-112">Bağımlı derlemelerin yeniden oluşturulması gerekmez, ya da herhangi bir kaynak kod değişikliği gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="019c2-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="019c2-113">İkili uyumlu değişiklikler de kaynak ile uyumlu değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="019c2-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="019c2-114">Kaynak ile uyumlu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="019c2-114">Source compatible changes</span></span>

<span data-ttu-id="019c2-115">Kitaplığınızda yapılan değişiklikler, kitaplığınızı kullanan uygulamalar ve kitaplıklar kaynak kodu değişiklikleri gerektirmiyorsa kaynak **uyumludur** , ancak kaynağın doğru çalışması için yeni sürüme yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="019c2-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="019c2-116">Uyumsuz değişiklikler</span><span class="sxs-lookup"><span data-stu-id="019c2-116">Incompatible changes</span></span>

<span data-ttu-id="019c2-117">Bir değişiklik, **kaynak uyumlu** veya **ikili uyumlu**değilse, bağımlı kitaplıklar ve uygulamalarda yeniden derleme ile birlikte kaynak kodu değişiklikleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="019c2-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="019c2-118">Kitaplığınızı değerlendirin</span><span class="sxs-lookup"><span data-stu-id="019c2-118">Evaluate your library</span></span>

<span data-ttu-id="019c2-119">Bu uyumluluk kavramları, kendi iç uygulamasına değil, kitaplığınız için ortak ve korumalı bildirimleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="019c2-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="019c2-120">Yeni özellikleri dahili olarak benimseme her zaman **ikili uyumludur**.</span><span class="sxs-lookup"><span data-stu-id="019c2-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="019c2-121">**İkili uyumlu** değişiklikler, eski sözdizimi olarak genel bildirimler için aynı derlenmiş kodu oluşturan yeni bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="019c2-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="019c2-122">Örneğin, bir yöntemi ifade olarak değiştirmek-Bodied üyesi, **ikili uyumlu** bir değişiklik olur:</span><span class="sxs-lookup"><span data-stu-id="019c2-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="019c2-123">Özgün kod:</span><span class="sxs-lookup"><span data-stu-id="019c2-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="019c2-124">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="019c2-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="019c2-125">**Kaynak ile uyumlu** değişiklikler ortak üye için derlenen kodu değiştiren, ancak mevcut çağrı siteleriyle uyumlu bir şekilde bir sözdizimi sunar.</span><span class="sxs-lookup"><span data-stu-id="019c2-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="019c2-126">Örneğin, bir by değeri parametresindeki bir yöntem imzasını bir `in` başvuru parametresine değiştirmek, kaynak uyumludur, ancak ikili uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="019c2-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="019c2-127">Özgün kod:</span><span class="sxs-lookup"><span data-stu-id="019c2-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="019c2-128">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="019c2-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="019c2-129">Genel bildirimleri etkileyen bir özelliğin tanıtımı, kaynak ile uyumlu veya ikili uyumlu olduğunu gösteren [Yeni](index.md) makalelerdir.</span><span class="sxs-lookup"><span data-stu-id="019c2-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
