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
ms.openlocfilehash: 8aafd1586068dcd7aaf4a72ef5454e3a2698ccd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397097"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="b710b-102">Özel Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="b710b-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="b710b-103">Öznitelikleri program öğelerle ilişkili eklendikten sonra yansıma mevcut olmaları ve değerleri sorgulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b710b-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="b710b-104">.NET Framework sürüm 1.0 ve 1.1'da, özel öznitelikler yürütme bağlamı incelenir.</span><span class="sxs-lookup"><span data-stu-id="b710b-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="b710b-105">.NET Framework sürüm 2.0, yeni bir yük bağlamı için yürütme yüklenemiyor kodu incelemek için kullanılan salt yansıma bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b710b-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="b710b-106">Yalnızca yansıma bağlamı</span><span class="sxs-lookup"><span data-stu-id="b710b-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="b710b-107">Yalnızca yansıma bağlamına yüklenen kod yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="b710b-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="b710b-108">Kendi oluşturucular yürütülmesi gerekir çünkü bu, özel öznitelikler örneklerini oluşturulamayacağını, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b710b-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="b710b-109">Yük ve salt yansıma bağlamına özel öznitelikleri incelemek için kullanmak <xref:System.Reflection.CustomAttributeData> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b710b-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="b710b-110">Statik uygun aşırı yüklemesine kullanarak bu sınıfın örnekleri, edinebilirsiniz <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b710b-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b710b-111">Bkz: [nasıl yapılır: salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="b710b-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="b710b-112">Yürütme bağlamı</span><span class="sxs-lookup"><span data-stu-id="b710b-112">The Execution Context</span></span>  
 <span data-ttu-id="b710b-113">Yürütme bağlamı sorgu öznitelikleri için ana yansıma yöntemleri <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> ve <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b710b-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b710b-114">Özel bir öznitelik erişilebilirliğini ekli olduğu derleme göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b710b-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="b710b-115">Bu, bir tür özel öznitelik bağlı olduğu derlemesindeki bir yöntem özel öznitelik Oluşturucusu çağırıp çağırmayacağınızı denetimini eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b710b-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="b710b-116">Gibi yöntemler <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> görünürlük ve tür bağımsız değişkeni erişilebilirliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b710b-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="b710b-117">Kullanıcı tanımlı türünü içeren bütünleştirilmiş kod türünü kullanarak özel bir öznitelik alabilir yalnızca **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="b710b-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="b710b-118">Aşağıdaki C# tipik özel öznitelik tasarım deseni örnektir.</span><span class="sxs-lookup"><span data-stu-id="b710b-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="b710b-119">Çalışma zamanı özel öznitelik yansıma modeli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b710b-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
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
  
 <span data-ttu-id="b710b-120">Genel özel öznitelik türü için bir özel öznitelikler almak çalışma zamanı girişiminde bulunursa <xref:System.ComponentModel.DescriptionAttribute> bağlı **GetLanguage** yöntemi, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="b710b-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="b710b-121">Çalışma zamanı denetleyen tür bağımsız değişkeni **DescriptionAttribute** için **Type.GetCustomAttributes**(türü *türü*) ortaktır ve bu nedenle görünür ve erişilebilir olduğunu.</span><span class="sxs-lookup"><span data-stu-id="b710b-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="b710b-122">Çalışma zamanı denetleyen kullanıcı tanımlı tür **MyDescriptionAttribute** öğesinden türetilen **DescriptionAttribute** görünür ve içinde erişilebilir **System.Web.DLL**derleme, yönteme bağlı **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="b710b-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="b710b-123">Çalışma zamanı denetleyen oluşturucusunun **MyDescriptionAttribute** görünür ve içinde erişilebilir **System.Web.DLL** derleme.</span><span class="sxs-lookup"><span data-stu-id="b710b-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="b710b-124">Çalışma zamanı oluşturucusunun çağırır **MyDescriptionAttribute** özel öznitelik parametrelerle ve çağıran için yeni bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="b710b-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="b710b-125">Özel öznitelik yansıma model türünün tanımlandığı derleme dışına kullanıcı tanımlı türler örneklerini sızıntısı.</span><span class="sxs-lookup"><span data-stu-id="b710b-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="b710b-126">Bu, kullanıcı tanımlı türler örneklerini gibi dönüş üyelerinden çalışma zamanı sistem Kitaplığı'nda farklı değildir <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> bir dizi döndürme **RuntimeMethodInfo** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b710b-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="b710b-127">Kullanıcı tanımlı özel öznitelik türü bulan bilgilerini istemciden önlemek için ortak olmayan olması için türün üyeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b710b-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="b710b-128">Aşağıdaki örnek, özel öznitelikler erişmek için yansıma kullanarak en temel yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b710b-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b710b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b710b-129">See Also</span></span>  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b710b-130">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b710b-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="b710b-131">Yansımayla İlgili Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="b710b-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
