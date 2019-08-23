---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 9b4322d83ad43cd3e49647df49c15bb5c917e1be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924098"
---
# <a name="reflection-c"></a><span data-ttu-id="36357-102">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="36357-102">Reflection (C#)</span></span>
<span data-ttu-id="36357-103">Yansıma derlemeleri, modülleri ve türleri <xref:System.Type>tanımlayan nesneler (türü) sağlar.</span><span class="sxs-lookup"><span data-stu-id="36357-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="36357-104">Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36357-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="36357-105">Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="36357-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="36357-106">Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="36357-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="36357-107">Bir değişkenin türünü almak için `GetType` `Object` temel sınıftan tüm türler tarafından devralınan statik yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="36357-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="36357-108">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="36357-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="36357-109">Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="36357-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="36357-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="36357-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> <span data-ttu-id="36357-111">C# Anahtar sözcükler `protected` ve`internal` Il 'de hiçbir anlamı yoktur ve yansıma API 'lerinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="36357-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="36357-112">Il 'deki ilgili terimler *Aile* ve derlemedir.</span><span class="sxs-lookup"><span data-stu-id="36357-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="36357-113">Yansıma kullanarak bir `internal` yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="36357-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="36357-114">Bir `protected internal` yöntemi tanımlamak için öğesini <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>kullanın.</span><span class="sxs-lookup"><span data-stu-id="36357-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="36357-115">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="36357-115">Reflection Overview</span></span>  
 <span data-ttu-id="36357-116">Aşağıdaki durumlarda yansıma yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="36357-116">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="36357-117">Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="36357-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="36357-118">Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="36357-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="36357-119">Bir derlemedeki türleri İnceleme ve örnekleme için.</span><span class="sxs-lookup"><span data-stu-id="36357-119">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="36357-120">Çalışma zamanında yeni türler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="36357-120">For building new types at runtime.</span></span> <span data-ttu-id="36357-121">İçinde <xref:System.Reflection.Emit>sınıfları kullanın.</span><span class="sxs-lookup"><span data-stu-id="36357-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="36357-122">Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme.</span><span class="sxs-lookup"><span data-stu-id="36357-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="36357-123">[Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="36357-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36357-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="36357-124">Related Sections</span></span>  
 <span data-ttu-id="36357-125">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="36357-125">For more information:</span></span>  
  
- [<span data-ttu-id="36357-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="36357-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="36357-127">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="36357-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="36357-128">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="36357-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="36357-129">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="36357-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="36357-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36357-130">See also</span></span>

- [<span data-ttu-id="36357-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="36357-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36357-132">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="36357-132">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
