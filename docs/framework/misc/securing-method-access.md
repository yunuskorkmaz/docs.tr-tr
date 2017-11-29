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
# <a name="securing-method-access"></a>Yöntem Erişiminin Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bazı yöntemleri çağırmak rasgele güvenilmeyen kod izin vermek uygun olmayabilir. Çeşitli riskleri tür yöntem neden: yöntemi kısıtlı bazı bilgiler; sağlayabilir kendisine geçirilen herhangi bir bilgi düşünüyorsanız; parametreleri denetlenirken hata yapmak; veya yanlış parametrelere sahip olabilir arıza ya da zararlı bir şeyler. Bu örneklerini unutmayın ve yöntemi korunmasına yardımcı olmak için bir eylem gerçekleştirmeniz gerekir.  
  
 Bazı durumlarda, ortak kullanılmak üzere tasarlanmamıştır, ancak hala ortak olmalıdır yöntemleri kısıtlamak gerekebilir. Örneğin, kendi DLL'leri arasında çağrılması gereken bir arabirim olabilir ve bu nedenle ortak olması gerekir, ancak genel olarak müşteriler kullanmasını önlemek için veya kötü amaçlı kod bileşeniniz Giriş noktasına yararlanmasını önlemek için kullanıma sunmak istediğiniz değil. Bir yöntemini kısıtlamak için başka bir yaygın nedeni genel kullanım için belirtmezseniz (ancak, olmalıdır ortak) belge ve ne çok iç arabirimde olabilir desteklemek zorunda kalmamak için.  
  
 Yöntem erişimi kısıtlamak için kod teklifleri çeşitli yollardan yönetilen:  
  
-   Güvenilen olabiliyorsa sınıfı, derleme veya türetilmiş sınıflar için erişilebilirlik kapsamını sınırlandırabilirsiniz. Yöntem erişimi sınırlamak için en basit yolu budur. Bazı durumlarda üst sınıfın kimliğini paylaştıkları karşın, genel olarak, türetilmiş sınıfları unutmayın bunlar, türetilen sınıf daha az güvenli olabilir. Güven from anahtar sözcüğü özel olarak Infer değil **korumalı**, değil mutlaka kullanılan güvenlik bağlamı.  
  
-   Belirli bir kimlik--esas olarak, tüm belirli arayanlar yöntemi erişimi sınırlamak [kanıt](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (tanımlayıcı ad, yayımcı, bölge vb.), seçin.  
  
-   Seçtiğiniz hangi izinlere sahip arayanlara yöntemi erişimi sınırlayın.  
  
 Benzer şekilde, bildirim temelli güvenlik, sınıflar, devralma denetlemenizi sağlar. Kullanabileceğiniz **InheritanceDemand** aşağıdakileri yapmak için:  
  
-   Türetilen sınıflar belirtilen kimlik veya iznine sahip olması gerekir.  
  
-   Belirtilen kimlik veya iznine sahip olması için belirli yöntemleri geçersiz kılmak türetilen sınıflar gerektirir.  
  
 Aşağıdaki örnek, sınırlı erişim için genel bir sınıf arayanlar belirli bir tanımlayıcı ad ile imzalanması gerektirerek korunmasına nasıl yardımcı olacağını gösterir. Bu örnekte <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> ile bir **talep** güçlü adı. Görev tabanlı bir derlemeyi tanımlayıcı adla imzalama hakkında bilgi için bkz: [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama  
 Kısmen güvenilen kod tarafından kullanılan sınıflar ve yöntemler, yanı sıra özelliklerini ve olaylar, engellemek için bu bölümde gösterilen bildirimleri kullanın. Bir sınıfa bu bildirimleri uygulayarak koruma tüm yöntemler, özellikler ve olayları için geçerlidir; Ancak, alan erişimi bildirimsel güvenliği tarafından etkilenmez unutmayın. Ayrıca, bağlantı talepleri yalnızca anında arayanlar karşı korumaya yardımcı olmak ve hala saldırıları luring tabi olabilir unutmayın.  
  
> [!NOTE]
>  Yeni bir saydamlık modeli de sunulan [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modeli tanımlayan güvenli koduyla <xref:System.Security.SecurityCriticalAttribute> özniteliği. Güvenlik açısından kritik kod arayanlar ve notlar tam güvenilir olmasını gerektirir. Kod erişim güvenliği kuralları altında önceki .NET Framework sürümlerini çalıştıran derlemeleri Düzey 2 derlemeler çağırabilirsiniz. Bu durumda, güvenlik açısından kritik öznitelikleri bağlantı talepleri için tam güven olarak kabul edilir.  
  
 Tanımlayıcı adlı derlemeler içinde bir [LinkDemand](../../../docs/framework/misc/link-demands.md) tüm genel olarak erişilebilir yöntemler, özellikler ve kullanımlarını tam güvenilen arayanlara okuduğunuzu kısıtlamak için olayları uygulanır. Bu özellik devre dışı bırakmak için uygulamalısınız <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu nedenle, açıkça güvenilmeyen arayanlar dışlanacak sınıfları işaretleme yalnızca imzasız derlemeler veya bu öznitelikle derlemeler için gereklidir; Bu bildirimler türlerinin bir alt okuduğunuzu işaretlemek için güvenilmeyen çağıranlar için tasarlanmamıştır kullanabilirsiniz.  
  
 Aşağıdaki örnekler, güvenilmeyen kod tarafından kullanılan sınıflar ve üyeleri önlemek nasıl gösterir.  
  
 Ortak nonsealed sınıflar için:  
  
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
  
 Genel sınıflar korumalı için:  
  
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
  
 Ortak soyut sınıflar için:  
  
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
  
 Genel sanal işlevleri için:  
  
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
  
 Ortak Özet işlevleri için:  
  
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
  
 Burada temel sınıfı tam güven talep olmayan ortak geçersiz kılma işlevleri için:  
  
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
  
 Burada temel sınıfı tam güven gerektiren ortak geçersiz kılma işlevleri için:  
  
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
  
 Genel arabirimler için:  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler  
  
> [!NOTE]
>  Bu bölümde bir yöntem olarak her ikisi de bildirirken bir güvenlik sorunu hakkında sizi uyarır `virtual` ve `internal` (`Overloads``Overridable``Friend` Visual Basic'te). Bu uyarı yalnızca .NET Framework sürümleri için 1.0 ve 1.1 geçerlidir, sonraki sürümleri için geçerli değil.  
  
 .NET Framework sürüm 1.0 ve 1.1, kodunuzu diğer derlemelerden kullanılamıyor onaylarken bir tür sistem erişilebilirlik ayrıntı farkında olmanız gerekir. Bildirilmiş bir yöntem **sanal** ve **iç** (**Overloads geçersiz kılınabilir arkadaş** Visual Basic'te) üst sınıfın vtable girişi geçersiz kılabilir ve yalnızca kullanılabilir aynı bütünleştirilmiş kod içinde iç olduğundan. Ancak, geçersiz kılma için erişilebilirlik göre belirlenir. **sanal** anahtar sözcüğü ve kodu sınıfı erişimi sürece başka bir derlemeden geçersiz olabilir. Bir geçersiz kılma olasılığını bir sorunu gösterir, bildirim temelli güvenlik düzeltmek veya kaldırmak için kullanırsanız **sanal** kesinlikle gerekli değilse anahtar sözcüğü.  
  
 Bu geçersiz kılmaları derleme hatası ile bir dil derleyici engeller olsa bile, geçersiz kılmak için diğer derleyicileri ile yazılan kod mümkündür olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
