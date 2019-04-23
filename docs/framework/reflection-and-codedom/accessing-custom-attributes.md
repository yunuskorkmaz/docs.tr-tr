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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 764b0d535413fc1e5e23a2e47221789aa807ff38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321737"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="a6b97-102">Özel Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="a6b97-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="a6b97-103">Öznitelikleri program öğelerle ilişkili eklendikten sonra yansıma olmaları ve uygulanmaları değerlerini sorgulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="a6b97-104">.NET Framework 1.0 ve 1.1 sürümlerinde, özel öznitelikler yürütme bağlamında incelenir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="a6b97-105">.NET Framework 2.0 sürümünde yeni bir yükleme bağlamı, yürütme için yüklenemiyor kodu incelemek için kullanılan salt yansıma bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6b97-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="a6b97-106">Yalnızca yansıma bağlamı</span><span class="sxs-lookup"><span data-stu-id="a6b97-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="a6b97-107">Salt yansıma bağlamına yüklenen kodunu yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="a6b97-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="a6b97-108">Oluşturucuları yürütülmesi gerekir çünkü bu, özel öznitelikler örneklerini oluşturulamayacağını, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="a6b97-109">Yük ve özel öznitelikleri salt yansıma bağlamında incelemek için kullandığınız <xref:System.Reflection.CustomAttributeData> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a6b97-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="a6b97-110">Bu sınıfın örnekleri statik uygun aşırı yüklemesini kullanarak elde edebilirsiniz <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6b97-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a6b97-111">Bkz: [nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="a6b97-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="a6b97-112">Yürütme bağlamı</span><span class="sxs-lookup"><span data-stu-id="a6b97-112">The Execution Context</span></span>  
 <span data-ttu-id="a6b97-113">Sorgu yürütme bağlamı özniteliklerle ana yansıma yöntemlerdir <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> ve <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6b97-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a6b97-114">Özel bir öznitelik erişilebilirliğini bağlı olduğu derleme göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="a6b97-115">Bu, özel öznitelik oluşturucusunun özel özniteliği ekli olduğu derlemedeki bir türe üzerinde bir yöntemi çağırıp çağırmayacağınızı denetimini eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="a6b97-116">Yöntemler gibi <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> görünürlük ve erişilebilirliği, tür bağımsız değişkeni kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="a6b97-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="a6b97-117">Kullanıcı tanımlı tür içeren derlemenin kod türünü kullanarak özel bir öznitelik alabilirsiniz yalnızca **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="a6b97-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="a6b97-118">Aşağıdaki C# tipik bir özel öznitelik tasarım deseni bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="a6b97-119">Bu, çalışma zamanı özel öznitelik yansıma modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```  
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
  
 <span data-ttu-id="a6b97-120">Genel özel öznitelik türü için özel öznitelikleri almak çalışma zamanı girişiminde bulunursa <xref:System.ComponentModel.DescriptionAttribute> bağlı **GetLanguage** yöntemi, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="a6b97-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="a6b97-121">Çalışma zamanı denetimleri tür bağımsız değişkeni **DescriptionAttribute** için **Type.GetCustomAttributes**(tür *türü*) herkese açıktır ve bu nedenle görünür ve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="a6b97-122">Çalışma zamanı denetimleri kullanıcı tanımlı türe **MyDescriptionAttribute** sınıfından türetilen **DescriptionAttribute** görünür ve erişilebilir **System.Web.DLL**derleme, yönteme bağlı **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="a6b97-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="a6b97-123">Çalışma zamanı denetimleri oluşturucusunun **MyDescriptionAttribute** görünür ve erişilebilir **System.Web.DLL** derleme.</span><span class="sxs-lookup"><span data-stu-id="a6b97-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="a6b97-124">Çalışma zamanı oluşturucusunu çağırır **MyDescriptionAttribute** özel öznitelik parametrelerle ve yeni nesne çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="a6b97-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="a6b97-125">Özel öznitelik yansıma model türünün tanımlandığı derleme dışından kullanıcı tanımlı türlerin örneklerini dışarıya sızmasına neden olabilecek.</span><span class="sxs-lookup"><span data-stu-id="a6b97-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="a6b97-126">Bu gibi kullanıcı tanımlı türler örneklerini döndüren üyelerinden sistem Çalışma Zamanı Kitaplığı'nda farklı değildir <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> dizisi döndürme **RuntimeMethodInfo** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a6b97-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="a6b97-127">Bir istemciden bir kullanıcı tanımlı özel öznitelik türü bulan bilgilerini önlemek için türün üyeleri özel olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a6b97-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="a6b97-128">Aşağıdaki örnek, özel özniteliklere erişim elde etmek için yansıma kullanarak en temel yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6b97-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a6b97-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b97-129">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a6b97-130">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a6b97-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="a6b97-131">Yansımayla İlgili Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="a6b97-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
