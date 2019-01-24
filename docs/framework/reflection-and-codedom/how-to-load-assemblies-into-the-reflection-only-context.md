---
title: 'Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eeef33745ebc8209fc7f69a9337af4093c1e8a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567054"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="f7281-102">Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme</span><span class="sxs-lookup"><span data-stu-id="f7281-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="f7281-103">Yalnızca yansıma yükleme bağlamı, diğer platformlar için veya .NET Framework'ün diğer sürümleri için derlenmiş derlemeleri incelemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7281-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="f7281-104">Bu bağlamı yüklenen kodunu yalnızca incelenebilir; yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="f7281-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="f7281-105">Oluşturucular yürütülemiyor çünkü bu nesneler oluşturulamayacağını, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7281-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="f7281-106">Kod olarak yürütülemiyor çünkü bağımlılıkları otomatik olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="f7281-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="f7281-107">Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f7281-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="f7281-108">Yük salt yansıma bağlamına bir derlemeyi yüklemek için</span><span class="sxs-lookup"><span data-stu-id="f7281-108">To load an assembly into the reflection-only load context</span></span>  
  
1.  <span data-ttu-id="f7281-109">Kullanım <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adı, verilen derlemeyi yüklemek için yöntem aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yolu verilen derlemeyi yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7281-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="f7281-110">Derleme ikili bir görüntüsüdür kullanırsanız <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="f7281-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7281-111">Yalnızca yansıma bağlam, .NET Framework sürümü yürütme bağlamı dışında bir sürümünden bir mscorlib.dll sürümü yüklemek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f7281-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2.  <span data-ttu-id="f7281-112">Derleme bağımlılıkları varsa <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi yüklenmemesi bunları.</span><span class="sxs-lookup"><span data-stu-id="f7281-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="f7281-113">Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f7281-113">If you need to examine them, you must load them yourself.</span></span>  
  
3.  <span data-ttu-id="f7281-114">Derlemenin kullanarak bir derleme salt yansıma bağlamına yüklü olup olmadığını <xref:System.Reflection.Assembly.ReflectionOnly%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7281-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4.  <span data-ttu-id="f7281-115">Öznitelikleri derlemenin veya derlemedeki türleri uygulandıysa, bu öznitelikleri kullanarak incelemek <xref:System.Reflection.CustomAttributeData> salt yansıma bağlamında kod yürütmesine girişimde bulunulmaz emin olmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f7281-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="f7281-116">Uygun aşırı yüklemesini kullanın <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> elde etmek için yöntemi <xref:System.Reflection.CustomAttributeData> bir derleme, üye, modül veya parametre uygulanan öznitelikleri temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f7281-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7281-117">Derleme veya içeriğine uygulanan öznitelikleri derlemede tanımlanan veya başka bir derlemede salt yansıma bağlamına yüklenen tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7281-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="f7281-118">Öznitelikleri tanımlandığı önceden bildirmek için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7281-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7281-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7281-119">Example</span></span>  
 <span data-ttu-id="f7281-120">Aşağıdaki kod örneği, salt yansıma bağlamına yüklenen bir derlemeye uygulanan öznitelikleri incelemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7281-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="f7281-121">Kod örneği, iki oluşturucu ve bir özellik ile özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7281-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="f7281-122">Öznitelik, derleme, derleme içinde bildirilen bir türe, türü bir yönteme ve yönteminin bir parametresi için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f7281-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="f7281-123">Yürütüldüğünde, derlemenin kendisi salt yansıma bağlamına yükler ve ona ve türler ve üyeler içerdiği için uygulanan özel öznitelikler hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f7281-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7281-124">Kod örneği basitleştirmek için derleme yükler ve kendisini inceler.</span><span class="sxs-lookup"><span data-stu-id="f7281-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="f7281-125">Normalde, yürütme bağlamı ve salt yansıma bağlamı yüklenen aynı derlemenin bulmak beklediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="f7281-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f7281-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7281-126">See also</span></span>
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
