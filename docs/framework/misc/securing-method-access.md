---
title: Yöntem Erişiminin Güvenliğini Sağlama
description: Genel kullanıma yönelik olmayan ancak hala public olması gereken yöntemler için yöntem erişimini güvenli hale getirme hakkında bilgi edinin.
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
ms.openlocfilehash: f9b9bc00058aefc8f58facff43509e717967c2a7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555724"
---
# <a name="securing-method-access"></a><span data-ttu-id="f3ecd-103">Yöntem Erişiminin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="f3ecd-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="f3ecd-104">Bazı yöntemler rastgele güvenilmeyen kodun çağrısına izin vermek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="f3ecd-105">Bu tür yöntemler çeşitli riskler sunar: yöntem bazı kısıtlı bilgiler verebilir; Bu, kendisine geçirilen bilgilere benzeyebilir; parametrelerde hata denetimi yapamayabilir; ya da yanlış parametrelerle hatalı olabilir veya zararlı bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="f3ecd-106">Bu durumları bilmeniz ve yöntemi korumanıza yardımcı olması için işlem yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="f3ecd-107">Bazı durumlarda, genel kullanım için tasarlanmamış ancak hala genel olması gereken yöntemleri kısıtlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="f3ecd-108">Örneğin, kendi dll 'larınız genelinde çağrılması gereken bir arayüze sahip olabilirsiniz ve bu nedenle genel olması gerekir, ancak müşterilerin bunu kullanmasını engellemek veya kötü amaçlı kodun giriş noktasını bileşeninize kötüye kullanmasını engellemek için genel kullanıma sunmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="f3ecd-109">Bir yöntemi genel kullanıma yönelik amaçlanmayan (ancak genel olması gereken) bir diğer yaygın nedeni, bir iç arabirim olabilecek özellikleri belgelemek ve desteklemek zorunda kalmamak.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="f3ecd-110">Yönetilen kod, yöntem erişimini kısıtlamak için çeşitli yollar sunar:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="f3ecd-111">Güveniliyorsa, erişilebilirlik kapsamını sınıf, derleme veya türetilmiş sınıflarla sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="f3ecd-112">Bu yöntem erişimini sınırlamanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="f3ecd-113">Genel olarak, türetilmiş sınıflar, türedikleri sınıftan daha az güvenilir olabilir, ancak bazı durumlarda üst sınıfın kimliğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="f3ecd-114">Özellikle, `protected` güvenlik bağlamında kullanılması gerekmeyen anahtar sözcükten güven çıkarmayın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="f3ecd-115">Belirli bir kimliğin çağıranlarını [(aslýnda](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) , The The Strong Name, Publisher, Zone vb.) ve seçtiğiniz bir kimliğe ait çağıranlara erişimi sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="f3ecd-116">Seçtiğiniz izinlere sahip çağıranlara erişim yöntemini sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="f3ecd-117">Benzer şekilde, bildirime dayalı güvenlik, sınıfların devralınmasını denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="f3ecd-118">**InheritanceDemand** kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="f3ecd-119">Türetilmiş sınıfların belirtilen kimliğe veya izne sahip olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="f3ecd-120">Belirli bir kimliğe veya izne sahip olacak şekilde belirli yöntemleri geçersiz kılan türetilmiş sınıflar gerektir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="f3ecd-121">Aşağıdaki örnek, çağıranların belirli bir tanımlayıcı ad ile imzalandığından emin olmak için genel bir sınıfı sınırlı erişim için nasıl koruyabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="f3ecd-122">Bu örnek, öğesini <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> tanımlayıcı ad için bir **talep** ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="f3ecd-123">Bir derlemeyi güçlü bir adla imzalama hakkında görev tabanlı bilgiler için, bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="f3ecd-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="f3ecd-124">Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama</span><span class="sxs-lookup"><span data-stu-id="f3ecd-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="f3ecd-125">Belirli sınıfların ve yöntemlerin yanı sıra özellik ve olayların kısmen güvenilen kod tarafından kullanılmasını engellemek için bu bölümde gösterilen bildirimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="f3ecd-126">Bu bildirimleri bir sınıfa uygulayarak, korumayı tüm yöntemlerine, özelliklerine ve olaylarına uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="f3ecd-127">Ancak, alan erişimi bildirime dayalı güvenlik tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="f3ecd-128">Ayrıca, bağlantı taleplerini yalnızca anında çağıranlara karşı korumaya yardımcı olur ve yine de söz konusu saldırı saldırılarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3ecd-129">.NET Framework 4 ' te yeni bir saydamlık modeli sunuldu.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="f3ecd-130">[Güvenlik açısından saydam kod, düzey 2](security-transparent-code-level-2.md) modeli, güvenli kodu <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="f3ecd-131">Güvenlik açısından kritik kod, çağıranların ve herıtors 'ın tamamen güvenilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="f3ecd-132">Önceki .NET Framework sürümlerinden kod erişimi güvenlik kuralları altında çalışan derlemeler, düzey 2 derlemelerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="f3ecd-133">Bu durumda, güvenlik açısından kritik öznitelikler tam güven için bağlantı talepleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="f3ecd-134">Tanımlayıcı adlı derlemelerde, bir [LinkDemand](link-demands.md) , kullanımlarını tam güvenilir çağıranlar olarak kısıtlamak için genel olarak erişilebilen tüm yöntemlere, özelliklere ve olaylara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="f3ecd-135">Bu özelliği devre dışı bırakmak için özniteliği uygulamanız gerekir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f3ecd-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="f3ecd-136">Bu nedenle, güvenilmeyen çağıranları hariç tutmak için sınıfları açıkça işaretlemek yalnızca imzasız derlemeler veya bu özniteliğe sahip derlemeler için gereklidir; Bu bildirimleri, güvenilmeyen çağıranlar için tasarlanmamış bir tür alt kümesini işaretlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="f3ecd-137">Aşağıdaki örneklerde, sınıfların ve üyelerin güvenilmeyen kod tarafından nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="f3ecd-138">Genel korumalı olmayan sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-138">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-139">Genel korumalı sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-139">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-140">Genel soyut sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-140">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-141">Genel sanal işlevler için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-141">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-142">Genel soyut işlevler için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-142">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-143">Genel geçersiz kılma işlevleri için, taban sınıfının tam güven talep etmez:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-143">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-144">Temel sınıfın tam güven talep ettiği genel geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-144">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="f3ecd-145">Ortak arabirimler için:</span><span class="sxs-lookup"><span data-stu-id="f3ecd-145">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="f3ecd-146">Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="f3ecd-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3ecd-147">Bu bölüm, bir yöntemi hem hem de (Visual Basic olarak) bildirirken bir güvenlik sorunuyla ilgili olarak uyarır `virtual` `internal` `Overloads` `Overridable` `Friend` .</span><span class="sxs-lookup"><span data-stu-id="f3ecd-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="f3ecd-148">Bu uyarı yalnızca 1,0 ve 1,1 .NET Framework sürümleri için geçerlidir, sonraki sürümler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="f3ecd-149">.NET Framework sürüm 1,0 ve 1,1 ' de, kodunuzun diğer derlemeler için kullanılamadığını onaylayarak sistem erişilebilirliği türünün farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="f3ecd-150">**Sanal** ve **iç** olarak belirtilen bir Yöntem (Visual Basic**geçersiz kılınabilir arkadaş aşırı yüklemeleri** ) üst sınıfın vtable girdisini geçersiz kılabilir ve yalnızca aynı bütünleştirilmiş kod içinden kullanılabilir çünkü iç.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="f3ecd-151">Ancak, geçersiz kılma için erişilebilirlik, **sanal** anahtar sözcüğü tarafından belirlenir ve bu kod, sınıfın kendine erişimi olduğu sürece başka bir derlemeden geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="f3ecd-152">Geçersiz kılma olasılığı bir sorun sunduğunda, sorunu gidermek için bildirime dayalı güvenlik kullanın ya da kesinlikle gerekmiyorsa **sanal** anahtar sözcüğünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="f3ecd-153">Bir dil derleyicisi bu geçersiz kılmaları derleme hatası ile engelseler de, diğer derleyicilerle yazılan kodun geçersiz kılınması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ecd-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3ecd-154">See also</span></span>

- [<span data-ttu-id="f3ecd-155">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f3ecd-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
