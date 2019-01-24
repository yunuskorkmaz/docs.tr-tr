---
title: Yansıma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 59910edda8e2dfc4ec8e697b1d5b9a0f47ff9dbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690117"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="a8f4c-102">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8f4c-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="a8f4c-103">Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="a8f4c-104">Yansıma, dinamik olarak bir türün bir örneğini oluşturmak, bağlama türü var olan bir nesneye veya türü mevcut bir nesneden elde ve kendi yöntemlerini çağırmak veya kendi alanlarına ve özelliklerine erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="a8f4c-105">Kodunuzda öznitelikler kullanıyorsanız, yansıma erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="a8f4c-106">Daha fazla bilgi için [öznitelikleri](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8f4c-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="a8f4c-107">Yansıma statik bir yöntemi kullanarak basit bir örnek `GetType` - tüm türleri tarafından devralınan `Object` temel sınıfı - bir değişken türü elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="a8f4c-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="a8f4c-108">Çıktı.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="a8f4c-109">Aşağıdaki örnek, yüklü bütünleştirilmiş kodun tam adı almak için yansıtma kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="a8f4c-110">Çıktı.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="a8f4c-111">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="a8f4c-111">Reflection Overview</span></span>  
 <span data-ttu-id="a8f4c-112">Yansıma, aşağıdaki durumlarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="a8f4c-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="a8f4c-113">Programınızın meta veri öznitelikleri erişmeye olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="a8f4c-114">Daha fazla bilgi için [öznitelikleri depolanan alınırken bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a8f4c-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="a8f4c-115">İnceleme ve derlemedeki türleri örnekleme için.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="a8f4c-116">Çalışma zamanında yeni türler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-116">For building new types at runtime.</span></span> <span data-ttu-id="a8f4c-117">Sınıfları kullanın <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="a8f4c-118">Çalışma zamanında oluşturulan türlerde yöntemleri erişme geç bağlama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="a8f4c-119">Konusuna [dinamik olarak yükleme ve türleri kullanarak](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8f4c-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8f4c-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a8f4c-120">Related Sections</span></span>  
 <span data-ttu-id="a8f4c-121">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="a8f4c-121">For more information:</span></span>  
  
-   [<span data-ttu-id="a8f4c-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a8f4c-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="a8f4c-123">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a8f4c-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="a8f4c-124">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a8f4c-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="a8f4c-125">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="a8f4c-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8f4c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f4c-126">See also</span></span>
- [<span data-ttu-id="a8f4c-127">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8f4c-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="a8f4c-128">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="a8f4c-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
