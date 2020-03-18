---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızda yeni dil özelliklerinin tanıtılması, onu kullanan kodu etkileyebilir.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399387"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="54e7f-103">C# geliştiricileri için sürüm ve güncelleştirme konuları</span><span class="sxs-lookup"><span data-stu-id="54e7f-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="54e7f-104">C# diline yeni özellikler eklendikçe uyumluluk çok önemli bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="54e7f-105">Hemen hemen her durumda, varolan kod herhangi bir sorun olmadan yeni bir derleyici sürümü ile yeniden derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="54e7f-106">Kitaplıkta yeni dil özelliklerini benimsediğinizde daha fazla özen gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="54e7f-107">En son sürümde bulunan özelliklere sahip yeni bir kitaplık oluşturuyor olabilirsiniz ve derleyicinin önceki sürümlerini kullanarak oluşturulmuş uygulamaların bu kitaplığı kullanabileceğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="54e7f-108">Veya varolan bir kitaplığı yükseltiyor olabilirsiniz ve kullanıcılarınızın çoğu henüz sürümlerini yükseltmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="54e7f-109">Yeni özellikleri benimseme konusunda karar vererken, iki uyumluluk varyasyonu göz önünde bulundurmanız gerekir: kaynak uyumluluğu ve ikili uyumlu.</span><span class="sxs-lookup"><span data-stu-id="54e7f-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="54e7f-110">İkili uyumlu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="54e7f-110">Binary compatible changes</span></span>

<span data-ttu-id="54e7f-111">Güncelleştirilmiş kitaplığınız, onu kullanan uygulamaları ve kitaplıkları yeniden oluşturmadan kullanılabildiğinde kitaplığınızdaki değişiklikler **ikili uyumludur.**</span><span class="sxs-lookup"><span data-stu-id="54e7f-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="54e7f-112">Bağımlı derlemelerin yeniden oluşturulması gerekmez veya kaynak kodu değişiklikleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="54e7f-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="54e7f-113">İkili uyumlu değişiklikler de kaynak uyumlu değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="54e7f-114">Kaynak uyumlu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="54e7f-114">Source compatible changes</span></span>

<span data-ttu-id="54e7f-115">Kitaplığınızı kullanan uygulamalar ve kitaplıklar kaynak kodu değişiklikleri gerektirmediğinde, kaynağın doğru çalışması için yeni sürüme karşı yeniden derlenmiş olması gerekirken kitaplığınızdaki değişiklikler **kaynak uyumludur.**</span><span class="sxs-lookup"><span data-stu-id="54e7f-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="54e7f-116">Uyumsuz değişiklikler</span><span class="sxs-lookup"><span data-stu-id="54e7f-116">Incompatible changes</span></span>

<span data-ttu-id="54e7f-117">Bir değişiklik ne **kaynak uyumlu** ne de ikili **uyumlu**ise, bağımlı kitaplıklarda ve uygulamalarda yeniden derleme ile birlikte kaynak kodu değişiklikleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54e7f-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="54e7f-118">Kitaplığınızı değerlendirin</span><span class="sxs-lookup"><span data-stu-id="54e7f-118">Evaluate your library</span></span>

<span data-ttu-id="54e7f-119">Bu uyumluluk kavramları, iç uygulamasını değil, kitaplığınız için genel ve korumalı bildirimleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="54e7f-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="54e7f-120">Herhangi bir yeni özelliği n içini dahili olarak benimsemek her zaman **ikili uyumludur.**</span><span class="sxs-lookup"><span data-stu-id="54e7f-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="54e7f-121">**İkili uyumlu** değişiklikler, eski sözdizimi yle aynı derlenmiş genel bildirimler için derlenmiş kodu oluşturan yeni sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="54e7f-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="54e7f-122">Örneğin, bir yöntemi ifade gövdeli bir üyeye değiştirmek **ikili uyumlu** bir değişikliktir:</span><span class="sxs-lookup"><span data-stu-id="54e7f-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="54e7f-123">Orijinal kod:</span><span class="sxs-lookup"><span data-stu-id="54e7f-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="54e7f-124">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="54e7f-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="54e7f-125">**Kaynak uyumlu** değişiklikler, derlenen bir üye için derlenen kodu, ancak varolan arama siteleriyle uyumlu bir şekilde değiştiren sözdizimini sunar.</span><span class="sxs-lookup"><span data-stu-id="54e7f-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="54e7f-126">Örneğin, bir yöntem imzasını bir değer parametresi ile referans parametreye `in` değiştirmek kaynak uyumludur, ancak ikili uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="54e7f-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="54e7f-127">Orijinal kod:</span><span class="sxs-lookup"><span data-stu-id="54e7f-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="54e7f-128">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="54e7f-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="54e7f-129">Ortak bildirimleri etkileyen bir özellik tanıtılması kaynak uyumlu veya ikili uyumlu [ise, yeni](index.md) makaleler ne notu.</span><span class="sxs-lookup"><span data-stu-id="54e7f-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
