---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711668"
---
# <a name="reflection-c"></a><span data-ttu-id="b5998-102">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="b5998-102">Reflection (C#)</span></span>

<span data-ttu-id="b5998-103">Yansıma, derlemeleri, <xref:System.Type>modülleri ve türleri açıklayan nesneler (tür) sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5998-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="b5998-104">Yansımayı dinamik olarak bir tür örneği oluşturmak, türü varolan bir nesneye bağlamak veya türü varolan bir nesneden almak ve yöntemlerini çağırmak veya alanlarına ve özelliklerine erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5998-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b5998-105">Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5998-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b5998-106">Daha fazla bilgi için [Özniteliklere](../../../standard/attributes/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b5998-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="b5998-107">Bir değişken türünü elde etmek <xref:System.Object.GetType> için `Object` temel sınıftan tüm türler tarafından devralınan yöntemi kullanarak yansımabasit bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5998-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="b5998-108">*.cs* `using System;` dosyanızın üst kısmında ve `using System.Reflection;` eklentisini yaptığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b5998-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="b5998-109">Çıktı: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="b5998-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="b5998-110">Aşağıdaki örnek, yüklenen derlemenin tam adını elde etmek için yansımayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5998-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="b5998-111">Çıktı: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="b5998-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="b5998-112">C# anahtar `protected` `internal` kelimeleri il'de bir anlam ifade etmez ve yansıma API'lerinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b5998-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="b5998-113">IL'de karşılık gelen terimler *Aile* ve *Meclis'tir.*</span><span class="sxs-lookup"><span data-stu-id="b5998-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="b5998-114">Yansımayı `internal` kullanarak bir yöntem <xref:System.Reflection.MethodBase.IsAssembly%2A> tanımlamak için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5998-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="b5998-115">Bir `protected internal` yöntemi tanımlamak için, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5998-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="b5998-116">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="b5998-116">Reflection overview</span></span>

<span data-ttu-id="b5998-117">Yansıma aşağıdaki durumlarda yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="b5998-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="b5998-118">Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="b5998-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b5998-119">Daha fazla bilgi için [bkz.](../../../standard/attributes/retrieving-information-stored-in-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="b5998-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="b5998-120">Montajdaki türleri incelemek ve anlık olarak incelemek için.</span><span class="sxs-lookup"><span data-stu-id="b5998-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="b5998-121">Çalışma zamanında yeni türler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b5998-121">For building new types at runtime.</span></span> <span data-ttu-id="b5998-122">Sınıfları <xref:System.Reflection.Emit>' da kullan.</span><span class="sxs-lookup"><span data-stu-id="b5998-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="b5998-123">Geç bağlama gerçekleştirmek için, çalışma zamanında oluşturulan türlerdeki yöntemlere erişin.</span><span class="sxs-lookup"><span data-stu-id="b5998-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b5998-124">Konuya Dinamik [Yükleme ve Kullanma Türleri'ni](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)görün.</span><span class="sxs-lookup"><span data-stu-id="b5998-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="b5998-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="b5998-125">Related sections</span></span>

<span data-ttu-id="b5998-126">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="b5998-126">For more information:</span></span>

- [<span data-ttu-id="b5998-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b5998-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="b5998-128">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b5998-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="b5998-129">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b5998-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="b5998-130">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="b5998-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="b5998-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5998-131">See also</span></span>

- [<span data-ttu-id="b5998-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b5998-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5998-133">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="b5998-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
