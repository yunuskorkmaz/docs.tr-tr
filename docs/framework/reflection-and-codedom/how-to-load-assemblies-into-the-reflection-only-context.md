---
title: 'Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme'
description: .NET 'teki yalnızca yansıma bağlamına derlemelerin nasıl yükleneceğini gösteren bir örnek görüntüleyin. Diğer platformlar veya .NET sürümleri için derlenen derlemeleri inceleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865079"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="119f4-104">Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme</span><span class="sxs-lookup"><span data-stu-id="119f4-104">How to: Load Assemblies into the Reflection-Only Context</span></span>

<span data-ttu-id="119f4-105">Yalnızca yansıma yük bağlamı, diğer platformlar veya .NET Framework diğer sürümleri için derlenen derlemeleri incelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="119f4-105">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="119f4-106">Bu içeriğe yüklenen kod yalnızca incelenebilir; yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="119f4-106">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="119f4-107">Bu, oluşturucular yürütülemediğinden nesnelerin oluşturulamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="119f4-107">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="119f4-108">Kod yürütülemediğinden, bağımlılıklar otomatik olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="119f4-108">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="119f4-109">Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="119f4-109">If you need to examine them, you must load them yourself.</span></span>

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="119f4-110">Bir derlemeyi yalnızca yansıma yükleme bağlamına yüklemek için</span><span class="sxs-lookup"><span data-stu-id="119f4-110">To load an assembly into the reflection-only load context</span></span>

1. <span data-ttu-id="119f4-111">Kendi <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adı verilen derlemeyi yüklemek için yöntem aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> kendi yolu verilen derlemeyi yüklemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="119f4-111">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="119f4-112">Derleme bir ikili görüntüdür, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntem aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="119f4-112">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>

    > [!NOTE]
    > <span data-ttu-id="119f4-113">mscorlib.dll sürümünü yürütme bağlamdaki sürümden farklı bir .NET Framework sürümüne yüklemek için yalnızca yansıma bağlamını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="119f4-113">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>

2. <span data-ttu-id="119f4-114">Derlemenin bağımlılıkları varsa, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi onları yüklemez.</span><span class="sxs-lookup"><span data-stu-id="119f4-114">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="119f4-115">Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="119f4-115">If you need to examine them, you must load them yourself.</span></span>

3. <span data-ttu-id="119f4-116">Derlemenin özelliğini kullanarak bir derlemenin yalnızca yansıma bağlamına yüklenip yüklenmediğini belirleme <xref:System.Reflection.Assembly.ReflectionOnly%2A> .</span><span class="sxs-lookup"><span data-stu-id="119f4-116">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>

4. <span data-ttu-id="119f4-117">Derleme için derlemeye veya derlemedeki türlere öznitelikler uygulanmışsa, <xref:System.Reflection.CustomAttributeData> yalnızca yansıma bağlamındaki kodu yürütmek için girişimde bulunmadığından emin olmak için sınıfını kullanarak bu öznitelikleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="119f4-117">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="119f4-118"><xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> <xref:System.Reflection.CustomAttributeData> Bir derlemeye, üyeye, modüle veya parametreye uygulanan öznitelikleri temsil eden nesneleri almak için yönteminin uygun aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="119f4-118">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>

    > [!NOTE]
    > <span data-ttu-id="119f4-119">Derlemeye veya içeriğine uygulanan öznitelikler derlemede tanımlanabilir veya yalnızca yansıma bağlamına yüklenmiş başka bir derlemede tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="119f4-119">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="119f4-120">Özniteliklerin tanımlandığı yerde önceden söylemek için bir yol yoktur.</span><span class="sxs-lookup"><span data-stu-id="119f4-120">There is no way to tell in advance where the attributes are defined.</span></span>

## <a name="example"></a><span data-ttu-id="119f4-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="119f4-121">Example</span></span>

<span data-ttu-id="119f4-122">Aşağıdaki kod örneği, yalnızca yansıma bağlamına yüklenmiş bir derlemeye uygulanan özniteliklerin nasıl inceleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="119f4-122">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>

<span data-ttu-id="119f4-123">Kod örneği, iki Oluşturucusu ve bir özelliği olan özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="119f4-123">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="119f4-124">Özniteliği derlemeye, derlemede tanımlanan bir türe, türünün bir yöntemine ve yönteminin parametresine uygulanır,.</span><span class="sxs-lookup"><span data-stu-id="119f4-124">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="119f4-125">Yürütüldüğünde, derleme kendisini yalnızca yansıma bağlamına yükler ve buna uygulanan özel öznitelikler ve içerdiği türler ve üyelere ilişkin bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="119f4-125">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>

> [!NOTE]
> <span data-ttu-id="119f4-126">Kod örneğini basitleştirmek için, derleme kendisini yükler ve inceler.</span><span class="sxs-lookup"><span data-stu-id="119f4-126">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="119f4-127">Normalde, hem yürütme bağlamına hem de yalnızca yansıma bağlamına yüklenmiş aynı derlemeyi bulmayı beklemez.</span><span class="sxs-lookup"><span data-stu-id="119f4-127">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="119f4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="119f4-128">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
