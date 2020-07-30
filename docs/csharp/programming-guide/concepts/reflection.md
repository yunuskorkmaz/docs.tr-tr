---
title: Yansıma (C#)
description: Yansıma, C# içindeki derlemeleri, modülleri ve türleri tanımlayan nesneler sağlar. Kodunuz öznitelikleri içeriyorsa, yansıma bunlara erişmenizi sağlar.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302808"
---
# <a name="reflection-c"></a><span data-ttu-id="db90a-104">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="db90a-104">Reflection (C#)</span></span>

<span data-ttu-id="db90a-105">Yansıma <xref:System.Type> derlemeleri, modülleri ve türleri tanımlayan nesneler (türü) sağlar.</span><span class="sxs-lookup"><span data-stu-id="db90a-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="db90a-106">Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db90a-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="db90a-107">Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="db90a-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="db90a-108">Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="db90a-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="db90a-109"><xref:System.Object.GetType> `Object` Bir değişkenin türünü almak için temel sınıftan tüm türler tarafından devralınan yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="db90a-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="db90a-110">`using System;` `using System.Reflection;` *. Cs* dosyanızın üst kısmına ve eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="db90a-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="db90a-111">Çıktı: `System.Int32` .</span><span class="sxs-lookup"><span data-stu-id="db90a-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="db90a-112">Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="db90a-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="db90a-113">Çıktı: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` .</span><span class="sxs-lookup"><span data-stu-id="db90a-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="db90a-114">C# anahtar sözcükleri `protected` ve `internal` Il 'de hiçbir anlamı yoktur ve yansıma API 'lerinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="db90a-114">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="db90a-115">Il 'deki ilgili terimler *Aile* ve *derlemedir*.</span><span class="sxs-lookup"><span data-stu-id="db90a-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="db90a-116">`internal`Yansıma kullanarak bir yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="db90a-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="db90a-117">Bir yöntemi tanımlamak için `protected internal` öğesini kullanın <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="db90a-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="db90a-118">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="db90a-118">Reflection overview</span></span>

<span data-ttu-id="db90a-119">Aşağıdaki durumlarda yansıma yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="db90a-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="db90a-120">Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="db90a-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="db90a-121">Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="db90a-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="db90a-122">Bir derlemedeki türleri İnceleme ve örnekleme için.</span><span class="sxs-lookup"><span data-stu-id="db90a-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="db90a-123">Çalışma zamanında yeni türler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="db90a-123">For building new types at runtime.</span></span> <span data-ttu-id="db90a-124">İçinde sınıfları kullanın <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="db90a-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="db90a-125">Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme.</span><span class="sxs-lookup"><span data-stu-id="db90a-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="db90a-126">[Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="db90a-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="db90a-127">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="db90a-127">Related sections</span></span>

<span data-ttu-id="db90a-128">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="db90a-128">For more information:</span></span>

- [<span data-ttu-id="db90a-129">Yansıma</span><span class="sxs-lookup"><span data-stu-id="db90a-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="db90a-130">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="db90a-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="db90a-131">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="db90a-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="db90a-132">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="db90a-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="db90a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db90a-133">See also</span></span>

- [<span data-ttu-id="db90a-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="db90a-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="db90a-135">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="db90a-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
