---
title: 'Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab0224dd0452003f1d43a314d03aaca0fe04fda
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="465d3-102">Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme</span><span class="sxs-lookup"><span data-stu-id="465d3-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="465d3-103">Yalnızca yansıma yükleme bağlamı, diğer platformlar için veya diğer .NET Framework sürümleri için derlenmiş derlemeleri incelemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="465d3-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="465d3-104">Bu bağlamına yüklenen kod yalnızca incelenebilir; yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="465d3-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="465d3-105">Oluşturucular yürütülemiyor çünkü bu nesneleri oluşturulamayacağını, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="465d3-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="465d3-106">Kod yürütülemiyor çünkü bağımlılıkları otomatik olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="465d3-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="465d3-107">Bunları inceleyin ihtiyacınız varsa, bunları kendiniz yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="465d3-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="465d3-108">Yalnızca yansıma yük bağlamına bir derlemeyi yüklemek için</span><span class="sxs-lookup"><span data-stu-id="465d3-108">To load an assembly into the reflection-only load context</span></span>  
  
1.  <span data-ttu-id="465d3-109">Kullanım <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adını, belirtilen derlemeyi yüklemeye yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yolunu verilen derlemeyi yüklemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="465d3-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="465d3-110">Derleme ikili görüntü ise kullanın <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntemi aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="465d3-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="465d3-111">Yalnızca yansıma bağlamı dışında yürütme bağlamı sürümünde .NET Framework sürümünün mscorlib.dll bir sürümünü yüklemek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="465d3-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2.  <span data-ttu-id="465d3-112">Derleme bağımlılıkları varsa <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi yüklenmemesi bunları.</span><span class="sxs-lookup"><span data-stu-id="465d3-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="465d3-113">Bunları inceleyin ihtiyacınız varsa, bunları kendiniz yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="465d3-113">If you need to examine them, you must load them yourself.</span></span>  
  
3.  <span data-ttu-id="465d3-114">Derlemenin kullanarak, bir derlemeyi salt yansıma bağlamına yüklü olup olmadığını belirlemek <xref:System.Reflection.Assembly.ReflectionOnly%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="465d3-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4.  <span data-ttu-id="465d3-115">Öznitelikleri derlemenin veya derlemedeki türleri uygulandıysa, bu öznitelikleri kullanarak inceleyin <xref:System.Reflection.CustomAttributeData> sınıfı salt yansıma bağlamında kod yürütmek için girişimde bulunulmaz emin olun.</span><span class="sxs-lookup"><span data-stu-id="465d3-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="465d3-116">Uygun kullanın <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> elde etmek için yöntemi <xref:System.Reflection.CustomAttributeData> bir derleme, üye, modül veya parametre uygulanan öznitelikleri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="465d3-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="465d3-117">Derleme veya içeriğinin uygulanan öznitelikleri derlemede tanımlanan veya başka bir derlemede salt yansıma bağlamına yüklenen tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="465d3-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="465d3-118">Önceden öznitelikleri tanımlandığı bildirmek için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="465d3-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="465d3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="465d3-119">Example</span></span>  
 <span data-ttu-id="465d3-120">Aşağıdaki kod örneğinde salt yansıma bağlamına yüklenen bir derleme uygulanan öznitelikleri inceleyin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="465d3-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="465d3-121">Kod örneği iki oluşturucular ve bir özellik ile özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="465d3-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="465d3-122">Öznitelik, derleme, derlemede bildirilen bir türe, türü yöntemi için ve yönteminin bir parametresi için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="465d3-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="465d3-123">Çalıştırıldığında, derleme kendisini salt yansıma bağlamına yükler ve onu ve türleri ve içerdiği üyelerine uygulanan özel öznitelikler hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="465d3-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="465d3-124">Kod örneği basitleştirmek için derleme yükler ve kendisini inceler.</span><span class="sxs-lookup"><span data-stu-id="465d3-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="465d3-125">Normalde, yürütme bağlamı ve yalnızca yansıma bağlam yüklenen aynı bütünleştirilmiş bulmak beklediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="465d3-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="465d3-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="465d3-126">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
