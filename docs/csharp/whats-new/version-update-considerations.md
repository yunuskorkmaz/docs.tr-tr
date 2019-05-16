---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızda yeni dil özellikleri ile tanışın, bunu kullanan kod etkileyebilir.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634485"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="a4588-103">C# geliştiricileri için sürüm ve güncelleştirme konuları</span><span class="sxs-lookup"><span data-stu-id="a4588-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="a4588-104">C# dili için yeni özellikler eklendikçe uyumluluk çok önemli bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="a4588-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="a4588-105">Hemen hemen tüm durumlarda, herhangi bir sorun olmadan yeni bir derleyici sürümü ile mevcut kodu yeniden derlenmesi.</span><span class="sxs-lookup"><span data-stu-id="a4588-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="a4588-106">Yeni dil özellikleri bir kitaplıkta benimsediğinizde, daha fazla dikkat gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4588-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="a4588-107">Yeni bir kitaplık en yeni sürümünde bulunan özellikler ile oluşturduğunuz ve derleyicinin önceki sürümleri kullanılarak oluşturulan uygulamaları sağlamak için kullanabilmesi.</span><span class="sxs-lookup"><span data-stu-id="a4588-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="a4588-108">Veya varolan bir kitaplığını yükseltme ve kullanıcılarınızın çoğu sürümler henüz yükseltilmemiş.</span><span class="sxs-lookup"><span data-stu-id="a4588-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="a4588-109">Yeni özellikler benimseme hakkında kararlar gibi uyumluluk iki çeşidi göz önünde bulundurmanız gerekir: kaynak uyumlu ve uyumlu ikili.</span><span class="sxs-lookup"><span data-stu-id="a4588-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="a4588-110">İkili uyumlu değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a4588-110">Binary compatible changes</span></span>

<span data-ttu-id="a4588-111">Değişiklikler kitaplığınıza **uyumlu ikili** zaman güncelleştirilmiş kitaplığınızı kullanılabilir uygulamaları ve kitaplıkları kullanan derlenmeden.</span><span class="sxs-lookup"><span data-stu-id="a4588-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="a4588-112">Bağımlı derlemelerin yeniden oluşturulması için gerekli değildir ve herhangi bir kaynak kod değişikliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4588-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="a4588-113">İkili uyumlu değişiklikleri de kaynak uyumlu değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="a4588-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="a4588-114">Kaynak uyumlu değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a4588-114">Source compatible changes</span></span>

<span data-ttu-id="a4588-115">Değişiklikler kitaplığınıza **kaynak uyumlu** zaman uygulamaları ve kitaplıkları, kitaplığı kullanan kaynak kod değişikliği gerektirmez, ancak kaynak düzgün çalışması için yeni sürümü karşı derlenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="a4588-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="a4588-116">Uyumsuz değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a4588-116">Incompatible changes</span></span>

<span data-ttu-id="a4588-117">Bir değişiklik ne ise **kaynak uyumlu** ya da **uyumlu ikili**, bağımlı kitaplıkları ve uygulamaları kaynak kodu değişiklikleri birlikte yeniden derleme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4588-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="a4588-118">Kitaplığınızı değerlendir</span><span class="sxs-lookup"><span data-stu-id="a4588-118">Evaluate your library</span></span>

<span data-ttu-id="a4588-119">Bu uyumluluk kavramları için kendi iç uygulama kitaplığınızın ortak ve korunan bildirimleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="a4588-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="a4588-120">Herhangi bir yeni özellik dahili olarak kullandığı her zaman **uyumlu ikili**.</span><span class="sxs-lookup"><span data-stu-id="a4588-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="a4588-121">**İkili uyumlu** değişiklikleri genel bildirimleri eski sözdizimi olarak aynı derlenmiş kodunu üretir yeni söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4588-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="a4588-122">Örneğin, bir ifade gövdeli üyesine bir yöntemi değiştirme olduğu bir **uyumlu ikili** değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a4588-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="a4588-123">Özgün kod:</span><span class="sxs-lookup"><span data-stu-id="a4588-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="a4588-124">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="a4588-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="a4588-125">**Kaynak uyumlu** değişikliğine neden söz dizimi genel bir üyenin, ancak mevcut çağrı siteleri bir şekilde uyumlu olarak derlenmiş kodunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a4588-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="a4588-126">Örneğin, bir yöntem imzasının değiştirilmesi bir değer parametresi tarafından bir `in` başvuruya göre kaynak uyumlu parametredir, ancak ikili uyumlu:</span><span class="sxs-lookup"><span data-stu-id="a4588-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="a4588-127">Özgün kod:</span><span class="sxs-lookup"><span data-stu-id="a4588-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="a4588-128">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="a4588-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="a4588-129">[Yenilikler](index.md) makaleleri ortak bildirimleri etkileyen bir özellik ile tanışın kaynak uyumlu ya da ikili uyumlu olup olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a4588-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
