---
description: 'Daha fazla bilgi edinin: yansıma (Visual Basic)'
title: Yansıma
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 532087f2ac32242b473d4524a6026519951d96d2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486816"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="99816-103">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99816-103">Reflection (Visual Basic)</span></span>

<span data-ttu-id="99816-104">Yansıma <xref:System.Type> derlemeleri, modülleri ve türleri tanımlayan nesneler (türü) sağlar.</span><span class="sxs-lookup"><span data-stu-id="99816-104">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="99816-105">Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99816-105">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="99816-106">Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99816-106">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="99816-107">Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="99816-107">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="99816-108">`GetType` `Object` Bir değişkenin türünü almak için temel sınıftan tüm türler tarafından devralınan statik yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99816-108">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="99816-109">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="99816-109">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="99816-110">Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="99816-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="99816-111">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="99816-111">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="99816-112">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="99816-112">Reflection Overview</span></span>  

 <span data-ttu-id="99816-113">Aşağıdaki durumlarda yansıma yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="99816-113">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="99816-114">Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="99816-114">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="99816-115">Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="99816-115">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="99816-116">Bir derlemedeki türleri İnceleme ve örnekleme için.</span><span class="sxs-lookup"><span data-stu-id="99816-116">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="99816-117">Çalışma zamanında yeni türler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="99816-117">For building new types at runtime.</span></span> <span data-ttu-id="99816-118">İçinde sınıfları kullanın <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="99816-118">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="99816-119">Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme.</span><span class="sxs-lookup"><span data-stu-id="99816-119">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="99816-120">[Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="99816-120">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99816-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="99816-121">Related Sections</span></span>  

 <span data-ttu-id="99816-122">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="99816-122">For more information:</span></span>  
  
- [<span data-ttu-id="99816-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="99816-123">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="99816-124">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="99816-124">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="99816-125">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="99816-125">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="99816-126">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="99816-126">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="99816-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99816-127">See also</span></span>

- [<span data-ttu-id="99816-128">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="99816-128">Visual Basic Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="99816-129">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="99816-129">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
