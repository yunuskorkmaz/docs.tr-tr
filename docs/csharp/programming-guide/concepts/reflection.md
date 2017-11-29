---
title: "Yansıma (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f567eb47d93fcd95e5895b4b44e1c89fb0b901b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-c"></a><span data-ttu-id="016fa-102">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="016fa-102">Reflection (C#)</span></span>
<span data-ttu-id="016fa-103">Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="016fa-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="016fa-104">Yansıma dinamik olarak bir türünün bir örneği oluşturmak, var olan bir nesne için bağ türü veya varolan bir nesneden türünü almak ve onun yöntemleri çağırma veya özellikleri ve alanları erişim için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="016fa-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="016fa-105">Kodunuzda öznitelikleri kullanıyorsanız, yansıma erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="016fa-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="016fa-106">Daha fazla bilgi için bkz: [öznitelikleri](https://msdn.microsoft.com/library/5x6cd29c).</span><span class="sxs-lookup"><span data-stu-id="016fa-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="016fa-107">Yansıma statik yöntemini kullanarak basit bir örneği burada verilmiştir `GetType` - tüm türlerinden tarafından devralınan `Object` temel sınıfı - değişken türünü almak için:</span><span class="sxs-lookup"><span data-stu-id="016fa-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="016fa-108">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="016fa-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="016fa-109">Aşağıdaki örnek yansıma yüklenen derlemenin tam adını almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="016fa-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="016fa-110">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="016fa-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="016fa-111">C# anahtar sözcükleri `protected` ve `internal` IL içinde hiçbir anlama sahip ve yansıma API'leri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="016fa-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="016fa-112">IL içinde karşılık gelen koşulları *ailesi* ve *derleme*.</span><span class="sxs-lookup"><span data-stu-id="016fa-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="016fa-113">Tanımlamak için bir `internal` yansıma, kullanım kullanarak yöntemi <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="016fa-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="016fa-114">Tanımlamak için bir `protected internal` yöntemi, kullanım <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="016fa-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="016fa-115">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="016fa-115">Reflection Overview</span></span>  
 <span data-ttu-id="016fa-116">Yansıma, aşağıdaki durumlarda yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="016fa-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="016fa-117">Öznitelikleri programınızın meta verilerde erişmek olduğunda.</span><span class="sxs-lookup"><span data-stu-id="016fa-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="016fa-118">Daha fazla bilgi için bkz: [öznitelikleri saklı alma bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="016fa-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="016fa-119">İncelenerek ve derlemedeki türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="016fa-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="016fa-120">Çalışma zamanında yeni türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="016fa-120">For building new types at runtime.</span></span> <span data-ttu-id="016fa-121">Sınıflarda kullanmak <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="016fa-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="016fa-122">Çalışma zamanında oluşturulan türleri yöntemlere erişme geç bağlama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="016fa-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="016fa-123">Konusuna [dinamik olarak yükleme ve türleri kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="016fa-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="016fa-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="016fa-124">Related Sections</span></span>  
 <span data-ttu-id="016fa-125">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="016fa-125">For more information:</span></span>  
  
-   [<span data-ttu-id="016fa-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="016fa-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="016fa-127">Tür bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="016fa-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="016fa-128">Yansıma ve genel türler</span><span class="sxs-lookup"><span data-stu-id="016fa-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="016fa-129">Özniteliklerde depolanan bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="016fa-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="016fa-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="016fa-130">See Also</span></span>  
 [<span data-ttu-id="016fa-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="016fa-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="016fa-132">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="016fa-132">Assemblies in the Common Language Runtime</span></span>](https://msdn.microsoft.com/library/k3677y81)
