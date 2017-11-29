---
title: "Yöntem Erişiminin Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 40d073a2ae390a434f5bf4562da7a6226993cfcb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-method-access"></a><span data-ttu-id="6f220-102">Yöntem Erişiminin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="6f220-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="6f220-103">Bazı yöntemleri çağırmak rasgele güvenilmeyen kod izin vermek uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f220-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="6f220-104">Çeşitli riskleri tür yöntem neden: yöntemi kısıtlı bazı bilgiler; sağlayabilir kendisine geçirilen herhangi bir bilgi düşünüyorsanız; parametreleri denetlenirken hata yapmak; veya yanlış parametrelere sahip olabilir arıza ya da zararlı bir şeyler.</span><span class="sxs-lookup"><span data-stu-id="6f220-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="6f220-105">Bu örneklerini unutmayın ve yöntemi korunmasına yardımcı olmak için bir eylem gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f220-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="6f220-106">Bazı durumlarda, ortak kullanılmak üzere tasarlanmamıştır, ancak hala ortak olmalıdır yöntemleri kısıtlamak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6f220-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="6f220-107">Örneğin, kendi DLL'leri arasında çağrılması gereken bir arabirim olabilir ve bu nedenle ortak olması gerekir, ancak genel olarak müşteriler kullanmasını önlemek için veya kötü amaçlı kod bileşeniniz Giriş noktasına yararlanmasını önlemek için kullanıma sunmak istediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="6f220-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="6f220-108">Bir yöntemini kısıtlamak için başka bir yaygın nedeni genel kullanım için belirtmezseniz (ancak, olmalıdır ortak) belge ve ne çok iç arabirimde olabilir desteklemek zorunda kalmamak için.</span><span class="sxs-lookup"><span data-stu-id="6f220-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="6f220-109">Yöntem erişimi kısıtlamak için kod teklifleri çeşitli yollardan yönetilen:</span><span class="sxs-lookup"><span data-stu-id="6f220-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="6f220-110">Güvenilen olabiliyorsa sınıfı, derleme veya türetilmiş sınıflar için erişilebilirlik kapsamını sınırlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f220-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="6f220-111">Yöntem erişimi sınırlamak için en basit yolu budur.</span><span class="sxs-lookup"><span data-stu-id="6f220-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="6f220-112">Bazı durumlarda üst sınıfın kimliğini paylaştıkları karşın, genel olarak, türetilmiş sınıfları unutmayın bunlar, türetilen sınıf daha az güvenli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f220-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="6f220-113">Güven from anahtar sözcüğü özel olarak Infer değil **korumalı**, değil mutlaka kullanılan güvenlik bağlamı.</span><span class="sxs-lookup"><span data-stu-id="6f220-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="6f220-114">Belirli bir kimlik--esas olarak, tüm belirli arayanlar yöntemi erişimi sınırlamak [kanıt](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (tanımlayıcı ad, yayımcı, bölge vb.), seçin.</span><span class="sxs-lookup"><span data-stu-id="6f220-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="6f220-115">Seçtiğiniz hangi izinlere sahip arayanlara yöntemi erişimi sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="6f220-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="6f220-116">Benzer şekilde, bildirim temelli güvenlik, sınıflar, devralma denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f220-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="6f220-117">Kullanabileceğiniz **InheritanceDemand** aşağıdakileri yapmak için:</span><span class="sxs-lookup"><span data-stu-id="6f220-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="6f220-118">Türetilen sınıflar belirtilen kimlik veya iznine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f220-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="6f220-119">Belirtilen kimlik veya iznine sahip olması için belirli yöntemleri geçersiz kılmak türetilen sınıflar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f220-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="6f220-120">Aşağıdaki örnek, sınırlı erişim için genel bir sınıf arayanlar belirli bir tanımlayıcı ad ile imzalanması gerektirerek korunmasına nasıl yardımcı olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f220-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="6f220-121">Bu örnekte <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> ile bir **talep** güçlü adı.</span><span class="sxs-lookup"><span data-stu-id="6f220-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="6f220-122">Görev tabanlı bir derlemeyi tanımlayıcı adla imzalama hakkında bilgi için bkz: [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6f220-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="6f220-123">Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama</span><span class="sxs-lookup"><span data-stu-id="6f220-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="6f220-124">Kısmen güvenilen kod tarafından kullanılan sınıflar ve yöntemler, yanı sıra özelliklerini ve olaylar, engellemek için bu bölümde gösterilen bildirimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f220-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="6f220-125">Bir sınıfa bu bildirimleri uygulayarak koruma tüm yöntemler, özellikler ve olayları için geçerlidir; Ancak, alan erişimi bildirimsel güvenliği tarafından etkilenmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f220-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="6f220-126">Ayrıca, bağlantı talepleri yalnızca anında arayanlar karşı korumaya yardımcı olmak ve hala saldırıları luring tabi olabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f220-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f220-127">Yeni bir saydamlık modeli de sunulan [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f220-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6f220-128">[Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modeli tanımlayan güvenli koduyla <xref:System.Security.SecurityCriticalAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6f220-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="6f220-129">Güvenlik açısından kritik kod arayanlar ve notlar tam güvenilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f220-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="6f220-130">Kod erişim güvenliği kuralları altında önceki .NET Framework sürümlerini çalıştıran derlemeleri Düzey 2 derlemeler çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f220-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="6f220-131">Bu durumda, güvenlik açısından kritik öznitelikleri bağlantı talepleri için tam güven olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6f220-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="6f220-132">Tanımlayıcı adlı derlemeler içinde bir [LinkDemand](../../../docs/framework/misc/link-demands.md) tüm genel olarak erişilebilir yöntemler, özellikler ve kullanımlarını tam güvenilen arayanlara okuduğunuzu kısıtlamak için olayları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f220-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="6f220-133">Bu özellik devre dışı bırakmak için uygulamalısınız <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6f220-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="6f220-134">Bu nedenle, açıkça güvenilmeyen arayanlar dışlanacak sınıfları işaretleme yalnızca imzasız derlemeler veya bu öznitelikle derlemeler için gereklidir; Bu bildirimler türlerinin bir alt okuduğunuzu işaretlemek için güvenilmeyen çağıranlar için tasarlanmamıştır kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f220-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="6f220-135">Aşağıdaki örnekler, güvenilmeyen kod tarafından kullanılan sınıflar ve üyeleri önlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f220-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="6f220-136">Ortak nonsealed sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="6f220-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="6f220-137">Genel sınıflar korumalı için:</span><span class="sxs-lookup"><span data-stu-id="6f220-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="6f220-138">Ortak soyut sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="6f220-138">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
```  
  
 <span data-ttu-id="6f220-139">Genel sanal işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="6f220-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="6f220-140">Ortak Özet işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="6f220-140">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="6f220-141">Burada temel sınıfı tam güven talep olmayan ortak geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="6f220-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="6f220-142">Burada temel sınıfı tam güven gerektiren ortak geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="6f220-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="6f220-143">Genel arabirimler için:</span><span class="sxs-lookup"><span data-stu-id="6f220-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="6f220-144">Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="6f220-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f220-145">Bu bölümde bir yöntem olarak her ikisi de bildirirken bir güvenlik sorunu hakkında sizi uyarır `virtual` ve `internal` (`Overloads``Overridable``Friend` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="6f220-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads``Overridable``Friend` in Visual Basic).</span></span> <span data-ttu-id="6f220-146">Bu uyarı yalnızca .NET Framework sürümleri için 1.0 ve 1.1 geçerlidir, sonraki sürümleri için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6f220-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="6f220-147">.NET Framework sürüm 1.0 ve 1.1, kodunuzu diğer derlemelerden kullanılamıyor onaylarken bir tür sistem erişilebilirlik ayrıntı farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f220-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="6f220-148">Bildirilmiş bir yöntem **sanal** ve **iç** (**Overloads geçersiz kılınabilir arkadaş** Visual Basic'te) üst sınıfın vtable girişi geçersiz kılabilir ve yalnızca kullanılabilir aynı bütünleştirilmiş kod içinde iç olduğundan.</span><span class="sxs-lookup"><span data-stu-id="6f220-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="6f220-149">Ancak, geçersiz kılma için erişilebilirlik göre belirlenir. **sanal** anahtar sözcüğü ve kodu sınıfı erişimi sürece başka bir derlemeden geçersiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f220-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="6f220-150">Bir geçersiz kılma olasılığını bir sorunu gösterir, bildirim temelli güvenlik düzeltmek veya kaldırmak için kullanırsanız **sanal** kesinlikle gerekli değilse anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6f220-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="6f220-151">Bu geçersiz kılmaları derleme hatası ile bir dil derleyici engeller olsa bile, geçersiz kılmak için diğer derleyicileri ile yazılan kod mümkündür olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f220-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f220-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f220-152">See Also</span></span>  
 [<span data-ttu-id="6f220-153">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6f220-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
