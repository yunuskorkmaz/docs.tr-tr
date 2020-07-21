---
title: Özel Özniteliklere Erişim
description: .NET 'teki özel özniteliklere erişin. Öznitelikler program öğeleriyle ilişkilendirildikten sonra, var olan ve değerlerini sorgulamak için yansıma kullanabilirsiniz.
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
ms.openlocfilehash: 1197fc5149e144d293deda1173e82ca2dadeda7d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475144"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="47248-104">Özel Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="47248-104">Accessing Custom Attributes</span></span>
<span data-ttu-id="47248-105">Öznitelikler program öğeleriyle ilişkilendirildikten sonra, var olan ve değerlerini sorgulamak için yansıma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47248-105">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="47248-106">.NET Framework sürüm 1,0 ve 1,1 ' de, özel öznitelikler yürütme bağlamında incelenir.</span><span class="sxs-lookup"><span data-stu-id="47248-106">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="47248-107">.NET Framework sürüm 2,0, yürütme için yüklenemeyen kodu incelemek için kullanılabilen yeni bir yükleme bağlamı (yalnızca yansıma bağlamı) sağlar.</span><span class="sxs-lookup"><span data-stu-id="47248-107">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="47248-108">Yalnızca yansıma bağlamı</span><span class="sxs-lookup"><span data-stu-id="47248-108">The Reflection-Only Context</span></span>  
 <span data-ttu-id="47248-109">Yalnızca yansıma bağlamına yüklenen kod yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="47248-109">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="47248-110">Bu, özel özniteliklerin örneklerinin oluşturulamadığını belirtir, çünkü bu, oluşturucuların yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47248-110">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="47248-111">Özel öznitelikleri yalnızca yansıma bağlamında yüklemek ve incelemek için <xref:System.Reflection.CustomAttributeData> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="47248-111">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="47248-112">Statik yöntemin uygun aşırı yüklemesini kullanarak bu sınıfın örneklerini elde edebilirsiniz <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="47248-112">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="47248-113">Bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="47248-113">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="47248-114">Yürütme bağlamı</span><span class="sxs-lookup"><span data-stu-id="47248-114">The Execution Context</span></span>  
 <span data-ttu-id="47248-115">Yürütme bağlamındaki öznitelikleri sorgulamak için ana yansıma yöntemleri <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> ve ' dir <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="47248-115">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="47248-116">Özel bir özniteliğin erişilebilirliği, eklendiği derlemeye göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="47248-116">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="47248-117">Bu, özel özniteliğin eklendiği derlemede bulunan bir türün bir yönteminin özel özniteliğin oluşturucusunu çağırıp çağıramayacağını denetlemeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="47248-117">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="47248-118"><xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType>Tür bağımsız değişkeninin görünürlüğünü ve erişilebilirliğini denetlemek gibi yöntemler.</span><span class="sxs-lookup"><span data-stu-id="47248-118">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="47248-119">Yalnızca Kullanıcı tanımlı türü içeren derlemede bulunan kod, **GetCustomAttributes**kullanarak bu türde özel bir öznitelik alabilir.</span><span class="sxs-lookup"><span data-stu-id="47248-119">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="47248-120">Aşağıdaki C# örneği tipik bir özel öznitelik tasarım deseninin örneğidir.</span><span class="sxs-lookup"><span data-stu-id="47248-120">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="47248-121">Çalışma zamanı özel öznitelik yansıma modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="47248-121">It illustrates the runtime custom attribute reflection model.</span></span>  
  
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
  
 <span data-ttu-id="47248-122">Çalışma zamanı, GetLanguage yöntemine iliştirilmiş ortak özel öznitelik türü için özel öznitelikleri almaya çalışıyorsa <xref:System.ComponentModel.DescriptionAttribute> , aşağıdaki eylemleri **GetLanguage** gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="47248-122">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="47248-123">Çalışma zamanı, **Type bağımsız değişkeni** **Type. GetCustomAttributes**(tür *türü*) public olup olmadığını denetler ve bu nedenle görünür ve erişilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="47248-123">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="47248-124">Çalışma zamanı, **DescriptionAttribute** 'dan türetilmiş Kullanıcı tanımlı **MyDescriptionAttribute** türünün görünür ve **System.Web.DLL** derlemesi içinde erişilebilir olup olmadığını denetler ve bu yöntem **GetLanguage**() yöntemine iliştirilir.</span><span class="sxs-lookup"><span data-stu-id="47248-124">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="47248-125">Çalışma zamanı, **MyDescriptionAttribute** oluşturucusunun **System.Web.DLL** derleme içinde görünür ve erişilebilir olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="47248-125">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="47248-126">Çalışma zamanı, **MyDescriptionAttribute** yapıcısını özel öznitelik parametreleriyle çağırır ve yeni nesneyi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="47248-126">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="47248-127">Özel öznitelik yansıtma modeli, Kullanıcı tanımlı türlerin, türün tanımlandığı derleme dışındaki örneklerini sızdırabilir.</span><span class="sxs-lookup"><span data-stu-id="47248-127">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="47248-128">Bu, çalışma zamanı sistem kitaplığındaki, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> **Runtimemethoınfo** nesnelerinin bir dizisini döndürmek gibi Kullanıcı tanımlı türlerin örneklerini döndüren üyelerden farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="47248-128">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="47248-129">Bir istemcinin Kullanıcı tanımlı bir özel öznitelik türü hakkında bilgi bulmasını engellemek için, tür üyelerini ortak olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="47248-129">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="47248-130">Aşağıdaki örnek, özel özniteliklere erişim sağlamak için yansıma kullanmanın temel yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47248-130">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="47248-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47248-131">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="47248-132">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="47248-132">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="47248-133">Yansımayla İlgili Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="47248-133">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
