---
title: Özel Özniteliklere Erişim
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: a5651e9dc8cf40e737dd523ec5d29e876a9c0765
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130296"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="240ad-102">Özel Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="240ad-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="240ad-103">Öznitelikler program öğeleriyle ilişkilendirildikten sonra, var olan ve değerlerini sorgulamak için yansıma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="240ad-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="240ad-104">.NET Framework sürüm 1,0 ve 1,1 ' de, özel öznitelikler yürütme bağlamında incelenir.</span><span class="sxs-lookup"><span data-stu-id="240ad-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="240ad-105">.NET Framework sürüm 2,0, yürütme için yüklenemeyen kodu incelemek için kullanılabilen yeni bir yükleme bağlamı (yalnızca yansıma bağlamı) sağlar.</span><span class="sxs-lookup"><span data-stu-id="240ad-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="240ad-106">Yalnızca yansıma bağlamı</span><span class="sxs-lookup"><span data-stu-id="240ad-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="240ad-107">Yalnızca yansıma bağlamına yüklenen kod yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="240ad-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="240ad-108">Bu, özel özniteliklerin örneklerinin oluşturulamadığını belirtir, çünkü bu, oluşturucuların yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="240ad-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="240ad-109">Özel öznitelikleri yalnızca yansıma bağlamında yüklemek ve incelemek için <xref:System.Reflection.CustomAttributeData> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="240ad-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="240ad-110">Statik <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> yöntemin uygun aşırı yüklemesini kullanarak bu sınıfın örneklerini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="240ad-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="240ad-111">Bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="240ad-111">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="240ad-112">Yürütme bağlamı</span><span class="sxs-lookup"><span data-stu-id="240ad-112">The Execution Context</span></span>  
 <span data-ttu-id="240ad-113">Yürütme bağlamındaki öznitelikleri sorgulamak için ana yansıma yöntemleri ve ' <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>dir.</span><span class="sxs-lookup"><span data-stu-id="240ad-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="240ad-114">Özel bir özniteliğin erişilebilirliği, eklendiği derlemeye göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="240ad-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="240ad-115">Bu, özel özniteliğin eklendiği derlemede bulunan bir türün bir yönteminin özel özniteliğin oluşturucusunu çağırıp çağıramayacağını denetlemeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="240ad-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="240ad-116">Tür bağımsız değişkeninin <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> görünürlüğünü ve erişilebilirliğini denetlemek gibi yöntemler.</span><span class="sxs-lookup"><span data-stu-id="240ad-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="240ad-117">Yalnızca Kullanıcı tanımlı türü içeren derlemede bulunan kod, **GetCustomAttributes**kullanarak bu türde özel bir öznitelik alabilir.</span><span class="sxs-lookup"><span data-stu-id="240ad-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="240ad-118">Aşağıdaki C# örneği tipik bir özel öznitelik tasarım deseninin örneğidir.</span><span class="sxs-lookup"><span data-stu-id="240ad-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="240ad-119">Çalışma zamanı özel öznitelik yansıma modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="240ad-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="240ad-120">Çalışma zamanı, <xref:System.ComponentModel.DescriptionAttribute> **GetLanguage** yöntemine iliştirilmiş ortak özel öznitelik türü için özel öznitelikleri almaya çalışıyorsa, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="240ad-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="240ad-121">Çalışma zamanı, **Type bağımsız değişkeni** **Type. GetCustomAttributes**(tür *türü*) public olup olmadığını denetler ve bu nedenle görünür ve erişilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="240ad-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="240ad-122">Çalışma zamanı, **DescriptionAttribute** 'dan türetilmiş Kullanıcı tanımlı **MyDescriptionAttribute** türünün görünür ve **System. Web. dll** derlemesi içinde erişilebilir olup olmadığını denetler. Bu, **GetLanguage**() yöntemine iliştirilir.</span><span class="sxs-lookup"><span data-stu-id="240ad-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="240ad-123">Çalışma zamanı, **MyDescriptionAttribute** oluşturucusunun, **System. Web. dll** derlemesi içinde görünür ve erişilebilir olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="240ad-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="240ad-124">Çalışma zamanı, **MyDescriptionAttribute** yapıcısını özel öznitelik parametreleriyle çağırır ve yeni nesneyi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="240ad-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="240ad-125">Özel öznitelik yansıtma modeli, Kullanıcı tanımlı türlerin, türün tanımlandığı derleme dışındaki örneklerini sızdırabilir.</span><span class="sxs-lookup"><span data-stu-id="240ad-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="240ad-126">Bu, çalışma zamanı sistem kitaplığındaki, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> **runtimemethoınfo** nesnelerinin bir dizisini döndürmek gibi Kullanıcı tanımlı türlerin örneklerini döndüren üyelerden farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="240ad-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="240ad-127">Bir istemcinin Kullanıcı tanımlı bir özel öznitelik türü hakkında bilgi bulmasını engellemek için, tür üyelerini ortak olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="240ad-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="240ad-128">Aşağıdaki örnek, özel özniteliklere erişim sağlamak için yansıma kullanmanın temel yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="240ad-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="240ad-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="240ad-129">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="240ad-130">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="240ad-130">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="240ad-131">Yansımayla İlgili Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="240ad-131">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
