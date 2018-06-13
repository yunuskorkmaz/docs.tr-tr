---
title: Yansıma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: f47f78ff9989fc44ad46b66a447061c3fa84a86e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646695"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="36e86-102">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36e86-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="36e86-103">Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36e86-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="36e86-104">Yansıma dinamik olarak bir türünün bir örneği oluşturmak, var olan bir nesne için bağ türü veya varolan bir nesneden türünü almak ve onun yöntemleri çağırma veya özellikleri ve alanları erişim için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36e86-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="36e86-105">Kodunuzda öznitelikleri kullanıyorsanız, yansıma erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="36e86-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="36e86-106">Daha fazla bilgi için bkz: [öznitelikleri](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="36e86-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="36e86-107">Yansıma statik yöntemini kullanarak basit bir örneği burada verilmiştir `GetType` - tüm türlerinden tarafından devralınan `Object` temel sınıfı - değişken türünü almak için:</span><span class="sxs-lookup"><span data-stu-id="36e86-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="36e86-108">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="36e86-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="36e86-109">Aşağıdaki örnek yansıma yüklenen derlemenin tam adını almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="36e86-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="36e86-110">Çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="36e86-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="36e86-111">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="36e86-111">Reflection Overview</span></span>  
 <span data-ttu-id="36e86-112">Yansıma, aşağıdaki durumlarda yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="36e86-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="36e86-113">Öznitelikleri programınızın meta verilerde erişmek olduğunda.</span><span class="sxs-lookup"><span data-stu-id="36e86-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="36e86-114">Daha fazla bilgi için bkz: [öznitelikleri saklı alma bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="36e86-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="36e86-115">İncelenerek ve derlemedeki türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="36e86-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="36e86-116">Çalışma zamanında yeni türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="36e86-116">For building new types at runtime.</span></span> <span data-ttu-id="36e86-117">Sınıflarda kullanmak <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="36e86-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="36e86-118">Çalışma zamanında oluşturulan türleri yöntemlere erişme geç bağlama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="36e86-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="36e86-119">Konusuna [dinamik olarak yükleme ve türleri kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="36e86-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36e86-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="36e86-120">Related Sections</span></span>  
 <span data-ttu-id="36e86-121">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="36e86-121">For more information:</span></span>  
  
-   [<span data-ttu-id="36e86-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="36e86-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="36e86-123">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="36e86-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="36e86-124">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="36e86-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="36e86-125">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="36e86-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="36e86-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36e86-126">See Also</span></span>  
 [<span data-ttu-id="36e86-127">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="36e86-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="36e86-128">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="36e86-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
