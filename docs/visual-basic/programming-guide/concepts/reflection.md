---
title: "Yansıma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2ae87eae971129059a7e84b36971c13a5fe71b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="e5e65-102">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5e65-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="e5e65-103">Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5e65-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="e5e65-104">Yansıma dinamik olarak bir türünün bir örneği oluşturmak, var olan bir nesne için bağ türü veya varolan bir nesneden türünü almak ve onun yöntemleri çağırma veya özellikleri ve alanları erişim için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e65-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="e5e65-105">Kodunuzda öznitelikleri kullanıyorsanız, yansıma erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e65-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="e5e65-106">Daha fazla bilgi için bkz: [öznitelikleri](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5e65-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="e5e65-107">Yansıma statik yöntemini kullanarak basit bir örneği burada verilmiştir `GetType` - tüm türlerinden tarafından devralınan `Object` temel sınıfı - değişken türünü almak için:</span><span class="sxs-lookup"><span data-stu-id="e5e65-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="e5e65-108">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="e5e65-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="e5e65-109">Aşağıdaki örnek yansıma yüklenen derlemenin tam adını almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5e65-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="e5e65-110">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="e5e65-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="e5e65-111">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="e5e65-111">Reflection Overview</span></span>  
 <span data-ttu-id="e5e65-112">Yansıma, aşağıdaki durumlarda yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="e5e65-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="e5e65-113">Öznitelikleri programınızın meta verilerde erişmek olduğunda.</span><span class="sxs-lookup"><span data-stu-id="e5e65-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="e5e65-114">Daha fazla bilgi için bkz: [öznitelikleri saklı alma bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e5e65-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="e5e65-115">İncelenerek ve derlemedeki türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e5e65-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="e5e65-116">Çalışma zamanında yeni türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e5e65-116">For building new types at runtime.</span></span> <span data-ttu-id="e5e65-117">Sınıflarda kullanmak <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="e5e65-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="e5e65-118">Çalışma zamanında oluşturulan türleri yöntemlere erişme geç bağlama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e5e65-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="e5e65-119">Konusuna [dinamik olarak yükleme ve türleri kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="e5e65-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5e65-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5e65-120">Related Sections</span></span>  
 <span data-ttu-id="e5e65-121">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="e5e65-121">For more information:</span></span>  
  
-   [<span data-ttu-id="e5e65-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e5e65-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="e5e65-123">Tür bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e5e65-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="e5e65-124">Yansıma ve genel türler</span><span class="sxs-lookup"><span data-stu-id="e5e65-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="e5e65-125">Özniteliklerde depolanan bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="e5e65-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5e65-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e65-126">See Also</span></span>  
 [<span data-ttu-id="e5e65-127">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5e65-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="e5e65-128">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="e5e65-128">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
