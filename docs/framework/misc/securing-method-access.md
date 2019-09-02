---
title: Yöntem Erişiminin Güvenliğini Sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1157d93585a564f83bf3809ba2fc3a26949fb711
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206121"
---
# <a name="securing-method-access"></a><span data-ttu-id="3af7c-102">Yöntem Erişiminin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="3af7c-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="3af7c-103">Bazı yöntemler rastgele güvenilmeyen kodun çağrısına izin vermek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="3af7c-104">Bu tür yöntemler çeşitli riskler oluşturmaktadır: Yöntem bazı kısıtlı bilgiler sağlayabilir; Bu, kendisine geçirilen bilgilere benzeyebilir; parametrelerde hata denetimi yapamayabilir; ya da yanlış parametrelerle hatalı olabilir veya zararlı bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="3af7c-105">Bu durumları bilmeniz ve yöntemi korumanıza yardımcı olması için işlem yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="3af7c-106">Bazı durumlarda, genel kullanım için tasarlanmamış ancak hala genel olması gereken yöntemleri kısıtlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="3af7c-107">Örneğin, kendi dll 'larınız genelinde çağrılması gereken bir arayüze sahip olabilirsiniz ve bu nedenle genel olması gerekir, ancak müşterilerin bunu kullanmasını engellemek veya kötü amaçlı kodun giriş noktasını bileşeninize kötüye kullanmasını engellemek için genel kullanıma sunmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3af7c-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="3af7c-108">Bir yöntemi genel kullanıma yönelik amaçlanmayan (ancak genel olması gerekir) bir diğer yaygın neden, çok dahili bir arabirim olabileceğini belgelemek ve desteklemek zorunda kalmamak.</span><span class="sxs-lookup"><span data-stu-id="3af7c-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="3af7c-109">Yönetilen kod, yöntem erişimini kısıtlamak için çeşitli yollar sunar:</span><span class="sxs-lookup"><span data-stu-id="3af7c-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="3af7c-110">Güveniliyorsa, erişilebilirlik kapsamını sınıf, derleme veya türetilmiş sınıflarla sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="3af7c-111">Bu yöntem erişimini sınırlamanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="3af7c-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="3af7c-112">Genel olarak, türetilmiş sınıfların türettikleri sınıftan daha az güvenilir olabileceğini, ancak bazı durumlarda üst sınıfın kimliğini paylaştıkları unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="3af7c-113">Özellikle, güvenlik bağlamında kullanılması gerekmeyen, **korunan**anahtar kelimeden güven çıkarmayın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="3af7c-114">Belirli bir kimliğin çağıranlarını (Aslýnda, The The Strong Name, Publisher, Zone [](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) vb.) ve seçtiğiniz bir kimliğe ait çağıranlara erişimi sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="3af7c-115">Seçtiğiniz izinlere sahip çağıranlara erişim yöntemini sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="3af7c-116">Benzer şekilde, bildirime dayalı güvenlik, sınıfların devralınmasını denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="3af7c-117">**InheritanceDemand** kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3af7c-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="3af7c-118">Türetilmiş sınıfların belirtilen kimliğe veya izne sahip olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="3af7c-119">Belirli bir kimliğe veya izne sahip olacak şekilde belirli yöntemleri geçersiz kılan türetilmiş sınıflar gerektir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="3af7c-120">Aşağıdaki örnek, çağıranların belirli bir tanımlayıcı ad ile imzalandığından emin olmak için genel bir sınıfı sınırlı erişim için nasıl koruyabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="3af7c-121">Bu örnek, <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> öğesini tanımlayıcı ad için bir **talep** ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="3af7c-122">Bir derlemeyi güçlü bir adla imzalama hakkında görev tabanlı bilgiler için, bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3af7c-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}   
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="3af7c-123">Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama</span><span class="sxs-lookup"><span data-stu-id="3af7c-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="3af7c-124">Belirli sınıfların ve yöntemlerin yanı sıra özellik ve olayların kısmen güvenilen kod tarafından kullanılmasını engellemek için bu bölümde gösterilen bildirimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="3af7c-125">Bu bildirimleri bir sınıfa uygulayarak, korumayı tüm yöntemlerine, özelliklerine ve olaylarına uygularsınız; Ancak, alan erişiminin bildirime dayalı güvenlik tarafından etkilenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="3af7c-126">Ayrıca, bağlantı taleplerini yalnızca anında çağıranlara karşı korumaya yardımcı olur ve yine de söz konusu saldırı saldırılarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3af7c-127">.NET Framework 4 ' te yeni bir saydamlık modeli sunuldu.</span><span class="sxs-lookup"><span data-stu-id="3af7c-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="3af7c-128">[Güvenlik açısından saydam kod, düzey 2](security-transparent-code-level-2.md) modeli, güvenli kodu <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3af7c-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="3af7c-129">Güvenlik açısından kritik kod, çağıranların ve herıtors 'ın tamamen güvenilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="3af7c-130">Önceki .NET Framework sürümlerinden kod erişimi güvenlik kuralları altında çalışan derlemeler, düzey 2 derlemelerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="3af7c-131">Bu durumda, güvenlik açısından kritik öznitelikler tam güven için bağlantı talepleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="3af7c-132">Tanımlayıcı adlı derlemelerde, bir [LinkDemand](link-demands.md) , kullanımlarını tam güvenilir çağıranlar olarak kısıtlamak için genel olarak erişilebilen tüm yöntemlere, özelliklere ve olaylara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="3af7c-133">Bu özelliği devre dışı bırakmak için <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="3af7c-134">Bu nedenle, güvenilmeyen çağıranları hariç tutmak için sınıfları açıkça işaretlemek yalnızca imzasız derlemeler veya bu özniteliğe sahip derlemeler için gereklidir; Bu bildirimleri, güvenilmeyen çağıranlar için tasarlanmamış bir tür alt kümesini işaretlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3af7c-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="3af7c-135">Aşağıdaki örneklerde, sınıfların ve üyelerin güvenilmeyen kod tarafından nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="3af7c-136">Genel korumalı olmayan sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-136">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _   
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="3af7c-137">Genel korumalı sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-137">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="3af7c-138">Genel soyut sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-138">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="3af7c-139">Genel sanal işlevler için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-139">For public virtual functions:</span></span>  
  
```vb  
Class Base1   
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1   
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="3af7c-140">Genel soyut işlevler için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-140">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="3af7c-141">Genel geçersiz kılma işlevleri için, taban sınıfının tam güven talep etmez:</span><span class="sxs-lookup"><span data-stu-id="3af7c-141">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="3af7c-142">Temel sınıfın tam güven talep ettiği genel geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-142">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe   
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="3af7c-143">Ortak arabirimler için:</span><span class="sxs-lookup"><span data-stu-id="3af7c-143">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe   
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="3af7c-144">Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="3af7c-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3af7c-145">`virtual` Bu bölüm, `internal` bir yöntemi hem hem de (`Overloads` `Overridable` `Friend` Visual Basic olarak) bildirirken bir güvenlik sorunuyla ilgili olarak uyarır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="3af7c-146">Bu uyarı yalnızca 1,0 ve 1,1 .NET Framework sürümleri için geçerlidir, sonraki sürümler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="3af7c-147">.NET Framework sürüm 1,0 ve 1,1 ' de, kodunuzun diğer derlemeler için kullanılamadığını onaylayarak sistem erişilebilirliği türünün farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="3af7c-148">**Sanal** ve **iç** olarak belirtilen bir Yöntem (Visual Basic**geçersiz kılınabilir arkadaş aşırı yüklemeleri** ) üst sınıfın vtable girdisini geçersiz kılabilir ve yalnızca aynı bütünleştirilmiş kod içinden kullanılabilir çünkü iç.</span><span class="sxs-lookup"><span data-stu-id="3af7c-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="3af7c-149">Ancak, geçersiz kılma için erişilebilirlik, **sanal** anahtar sözcüğü tarafından belirlenir ve bu kod, sınıfın kendine erişimi olduğu sürece başka bir derlemeden geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="3af7c-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="3af7c-150">Geçersiz kılma olasılığı bir sorun sunduğunda, sorunu gidermek için bildirime dayalı güvenlik kullanın ya da kesinlikle gerekmiyorsa **sanal** anahtar sözcüğünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3af7c-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="3af7c-151">Bir dil derleyicisi bu geçersiz kılmaları derleme hatası ile engelseler de, diğer derleyicilerle yazılmış kodların geçersiz kılınmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3af7c-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af7c-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3af7c-152">See also</span></span>

- [<span data-ttu-id="3af7c-153">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3af7c-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
