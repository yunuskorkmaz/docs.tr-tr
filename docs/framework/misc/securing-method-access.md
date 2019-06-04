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
ms.openlocfilehash: 8be971cee4aa2ae09745a090396269c80ca62198
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487953"
---
# <a name="securing-method-access"></a><span data-ttu-id="fc1d2-102">Yöntem Erişiminin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="fc1d2-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="fc1d2-103">Bazı yöntemleri çağırmak rastgele güvenilmeyen kod izin vermek uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="fc1d2-104">Bu tür yöntemler birkaç riskler konusunda sizi uyarmayı: Yöntemi, kısıtlı bazı bilgiler sağlayabilir; Bu, geçirilen herhangi bir bilgi düşünüyorsanız; üzerinde parametre denetlemede hata yapmanız; veya yanlış parametrelerle sitelerinin arıza yapmasına veya zararlı bir şey.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="fc1d2-105">Bu gibi durumlarda unutmayın ve yöntem korumaya yardımcı olmak amacıyla eyleme geçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="fc1d2-106">Bazı durumlarda, genel kullanım için değildir ancak yine de ortak olmalıdır yöntemleri kısıtlama gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="fc1d2-107">Örneğin, kendi DLL'leri çağrılması gereken bir arabirim olabilir ve bu nedenle ortak olmalıdır, ancak genel olarak müşterilerin kullanmasını önlemek için ya da kötü amaçlı kod bileşeniniz girdi noktası yararlanmasını önlemek için kullanıma sunmak istiyorsanız değil.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="fc1d2-108">Bir yöntemini kısıtlamak için başka bir yaygın nedeni genel kullanıma yönelik değildir (ancak getirilmesi gereken ortak) belgesi ve hangi çok iç arabirimi olabilir desteklemek üzere yapmamaya sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="fc1d2-109">Metot erişimini kısıtlamak için yönetilen kodu sunar birkaç yolu:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="fc1d2-110">Güvenilir olabilir, sınıf, derleme veya türetilmiş sınıflar erişilebilirlik kapsamını sınırlamak.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="fc1d2-111">Bu metot erişimini sınırlamak için en basit yoludur.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="fc1d2-112">Bazı durumlarda üst sınıfın kimliğini paylaştıkları rağmen genel olarak, türetilmiş sınıflar Not bunlar, türetilen sınıf daha az güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="fc1d2-113">Özellikle, güven from anahtar sözcüğü Infer değil **korumalı**, değil gerekmeyen kullanılan güvenlik bağlamı.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="fc1d2-114">Belirli bir kimlik--esas olarak, herhangi belirli arayanlar yöntemi erişimi sınırlamak [kanıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (tanımlayıcı ad, yayımcı, bölge vb.) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="fc1d2-115">Seçtiğiniz izinlere sahip arayanlara metot erişimini sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="fc1d2-116">Benzer şekilde, bildirim temelli güvenlik sınıf devralma denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="fc1d2-117">Kullanabileceğiniz **Inheritancedemand** aşağıdakileri yapmak için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="fc1d2-118">Türetilen sınıflar belirtilen kimlik veya iznine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="fc1d2-119">Belirtilen kimlik veya iznine sahip olması için belirli yöntemleri geçersiz kılan türetilmiş sınıflar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="fc1d2-120">Aşağıdaki örnek, Arayanların belirli bir tanımlayıcı ad ile imzalanması gerektirerek sınırlı erişim için genel bir sınıf korunmasına nasıl yardımcı olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="fc1d2-121">Bu örnekte <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> ile bir **isteğe** için tanımlayıcı ad.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="fc1d2-122">Görev tabanlı bir derlemeyi katı bir adla imzalamak hakkında bilgi için bkz. [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="fc1d2-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="fc1d2-123">Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama</span><span class="sxs-lookup"><span data-stu-id="fc1d2-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="fc1d2-124">Bu bölümde gösterilen bildirimler, kısmen güvenilen kod tarafından kullanılan sınıflar ve yöntemler, yanı sıra özellikleri ve olayları, engellemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="fc1d2-125">Bu bildirimleri bir sınıfa uygulandığında, koruma tüm, yöntemler, özellikler ve olaylar için geçerlidir; alan erişimini tarafından bildirim temelli güvenlik etkilenmez ancak unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="fc1d2-126">Ayrıca, bağlantı talepleri yalnızca anında arayanlar karşı korumaya yardımcı olmak ve hala saldırıları luring tabi olabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc1d2-127">Yeni bir saydamlık modeli, .NET Framework 4'te sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="fc1d2-128">[Güvenliği saydam kod, 2. düzey](../../../docs/framework/misc/security-transparent-code-level-2.md) modeli ile güvenli kod tanımlayan <xref:System.Security.SecurityCriticalAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="fc1d2-129">Güvenlik açısından kritik kod, Arayanların ve devralanlar tam güvenilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="fc1d2-130">Önceki .NET Framework sürümlerinden kod erişim güvenliği kuralları altında çalışan derlemeler, Düzey 2 derlemeler çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="fc1d2-131">Bu durumda, güvenlik açısından kritik öznitelikleri tam güven için bağlantı talepleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="fc1d2-132">Tanımlayıcı adlı derlemeler içinde bir [LinkDemand](../../../docs/framework/misc/link-demands.md) tüm genel olarak erişilebilir yöntemler, özellikler ve bunların kullanılması için tam olarak güvenilmeyen bir çağırıcıya sıralamadaki kısıtlamak için olayları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="fc1d2-133">Bu özellik devre dışı bırakmak için uygulamalısınız <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="fc1d2-134">Bu nedenle, güvenilmeyen çağıranlar dışlanacak sınıfları açıkça işaretleme yalnızca imzasız derlemeler veya bu özniteliğe sahip derlemeler için gereklidir. Güvenilmeyen arayanlar için amaçlanmayan türleri kümesini sıralamadaki işaretlemek için bu bildirimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="fc1d2-135">Aşağıdaki örnekler, güvenilmeyen kod tarafından kullanılan sınıflar ve üyeler önlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="fc1d2-136">Genel nonsealed sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-137">Sealed sınıfları public:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-138">Genel soyut sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-139">Genel sanal işlevler için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-140">Genel soyut işlevler için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-141">Burada temel sınıf tam güven isteğe bağlı olmayan genel bir geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-142">Burada temel sınıf tam güven gerektiren genel geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="fc1d2-143">Genel arabirimler için:</span><span class="sxs-lookup"><span data-stu-id="fc1d2-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="fc1d2-144">Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="fc1d2-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc1d2-145">Bu bölümde bir yöntem olarak bildirirken bir güvenlik sorunu hakkında uyarır `virtual` ve `internal` (`Overloads` `Overridable` `Friend` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="fc1d2-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="fc1d2-146">Bu uyarı yalnızca .NET Framework sürümleri için 1.0 ve 1.1 geçerlidir, daha sonraki sürümlere uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="fc1d2-147">.NET Framework sürüm 1.0 ve 1.1, kodunuzun diğer derlemeler için kullanılamaz olduğunu onaylama tür sistem erişilebilirliği'bir nuance farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="fc1d2-148">Bildirilen bir yöntemi **sanal** ve **iç** (**aşırı geçersiz kılınabilir arkadaş** Visual Basic'te) üst sınıfın vtable girişi geçersiz kılabilir ve yalnızca kullanılabilir aynı bütünleştirilmiş kod içinde iç olduğundan.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="fc1d2-149">Ancak, geçersiz kılmak için erişilebilirlik tarafından belirlenen **sanal** anahtar sözcüğü ve kod sınıfı erişiminin olduğu sürece başka bir bütünleştirilmiş koddan kılınmasına oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="fc1d2-150">Bir geçersiz kılma olası bir sorunu sunarsa, düzeltin veya kaldırmak için bildirime dayalı güvenlik kullanın **sanal** kati şekilde gerekli değilse, anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="fc1d2-151">Bir dil derleyicisi bir derleme hatası ile bu geçersiz kılmaları engelliyor olsa bile, bunu geçersiz kılmak için diğer derleyicilerle yazılan kod mümkün olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1d2-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc1d2-152">See also</span></span>

- [<span data-ttu-id="fc1d2-153">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fc1d2-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
