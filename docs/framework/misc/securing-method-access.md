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
ms.openlocfilehash: 51a7969821cb4c2367ac298c8452daf1f2a8ceab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185907"
---
# <a name="securing-method-access"></a>Yöntem Erişiminin Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bazı yöntemleri çağırmak rastgele güvenilmeyen kod izin vermek uygun olmayabilir. Bu tür yöntemler birkaç riskler konusunda sizi uyarmayı: yöntemi; kısıtlı bazı bilgiler sağlayabilir. Bu, geçirilen herhangi bir bilgi düşünüyorsanız; üzerinde parametre denetlemede hata yapmanız; veya yanlış parametrelerle sitelerinin arıza yapmasına veya zararlı bir şey. Bu gibi durumlarda unutmayın ve yöntem korumaya yardımcı olmak amacıyla eyleme geçmek gerekir.  
  
 Bazı durumlarda, genel kullanım için değildir ancak yine de ortak olmalıdır yöntemleri kısıtlama gerekebilir. Örneğin, kendi DLL'leri çağrılması gereken bir arabirim olabilir ve bu nedenle ortak olmalıdır, ancak genel olarak müşterilerin kullanmasını önlemek için ya da kötü amaçlı kod bileşeniniz girdi noktası yararlanmasını önlemek için kullanıma sunmak istiyorsanız değil. Bir yöntemini kısıtlamak için başka bir yaygın nedeni genel kullanıma yönelik değildir (ancak getirilmesi gereken ortak) belgesi ve hangi çok iç arabirimi olabilir desteklemek üzere yapmamaya sağlamaktır.  
  
 Metot erişimini kısıtlamak için yönetilen kodu sunar birkaç yolu:  
  
-   Güvenilir olabilir, sınıf, derleme veya türetilmiş sınıflar erişilebilirlik kapsamını sınırlamak. Bu metot erişimini sınırlamak için en basit yoludur. Bazı durumlarda üst sınıfın kimliğini paylaştıkları rağmen genel olarak, türetilmiş sınıflar Not bunlar, türetilen sınıf daha az güvenilir olabilir. Özellikle, güven from anahtar sözcüğü Infer değil **korumalı**, değil gerekmeyen kullanılan güvenlik bağlamı.  
  
-   Belirli bir kimlik--esas olarak, herhangi belirli arayanlar yöntemi erişimi sınırlamak [kanıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (tanımlayıcı ad, yayımcı, bölge vb.) öğesini seçin.  
  
-   Seçtiğiniz izinlere sahip arayanlara metot erişimini sınırlayın.  
  
 Benzer şekilde, bildirim temelli güvenlik sınıf devralma denetlemenizi sağlar. Kullanabileceğiniz **Inheritancedemand** aşağıdakileri yapmak için:  
  
-   Türetilen sınıflar belirtilen kimlik veya iznine sahip olması gerekir.  
  
-   Belirtilen kimlik veya iznine sahip olması için belirli yöntemleri geçersiz kılan türetilmiş sınıflar gerektirir.  
  
 Aşağıdaki örnek, Arayanların belirli bir tanımlayıcı ad ile imzalanması gerektirerek sınırlı erişim için genel bir sınıf korunmasına nasıl yardımcı olacağını gösterir. Bu örnekte <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> ile bir **isteğe** için tanımlayıcı ad. Görev tabanlı bir derlemeyi katı bir adla imzalamak hakkında bilgi için bkz. [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Bu bölümde gösterilen bildirimler, kısmen güvenilen kod tarafından kullanılan sınıflar ve yöntemler, yanı sıra özellikleri ve olayları, engellemek için kullanın. Bu bildirimleri bir sınıfa uygulandığında, koruma tüm, yöntemler, özellikler ve olaylar için geçerlidir; alan erişimini tarafından bildirim temelli güvenlik etkilenmez ancak unutmayın. Ayrıca, bağlantı talepleri yalnızca anında arayanlar karşı korumaya yardımcı olmak ve hala saldırıları luring tabi olabilir unutmayın.  
  
> [!NOTE]
>  Yeni bir saydamlık modeli içindeki sunulan [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Güvenliği saydam kod, 2. düzey](../../../docs/framework/misc/security-transparent-code-level-2.md) modeli ile güvenli kod tanımlayan <xref:System.Security.SecurityCriticalAttribute> özniteliği. Güvenlik açısından kritik kod, Arayanların ve devralanlar tam güvenilir olmasını gerektirir. Önceki .NET Framework sürümlerinden kod erişim güvenliği kuralları altında çalışan derlemeler, Düzey 2 derlemeler çağırabilirsiniz. Bu durumda, güvenlik açısından kritik öznitelikleri tam güven için bağlantı talepleri olarak kabul edilir.  
  
 Tanımlayıcı adlı derlemeler içinde bir [LinkDemand](../../../docs/framework/misc/link-demands.md) tüm genel olarak erişilebilir yöntemler, özellikler ve bunların kullanılması için tam olarak güvenilmeyen bir çağırıcıya sıralamadaki kısıtlamak için olayları uygulanır. Bu özellik devre dışı bırakmak için uygulamalısınız <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu nedenle, güvenilmeyen çağıranlar dışlanacak sınıfları açıkça işaretleme yalnızca imzasız derlemeler veya bu özniteliğe sahip derlemeler için gereklidir. Güvenilmeyen arayanlar için amaçlanmayan türleri kümesini sıralamadaki işaretlemek için bu bildirimleri kullanabilirsiniz.  
  
 Aşağıdaki örnekler, güvenilmeyen kod tarafından kullanılan sınıflar ve üyeler önlemek nasıl gösterir.  
  
 Genel nonsealed sınıflar için:  
  
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
  
 Sealed sınıfları public:  
  
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
  
 Genel soyut sınıflar için:  
  
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
  
 Genel sanal işlevler için:  
  
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
  
 Genel soyut işlevler için:  
  
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
  
 Burada temel sınıf tam güven isteğe bağlı olmayan genel bir geçersiz kılma işlevleri için:  
  
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
  
 Burada temel sınıf tam güven gerektiren genel geçersiz kılma işlevleri için:  
  
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
>  Bu bölümde bir yöntem olarak bildirirken bir güvenlik sorunu hakkında uyarır `virtual` ve `internal` (`Overloads``Overridable``Friend` Visual Basic'te). Bu uyarı yalnızca .NET Framework sürümleri için 1.0 ve 1.1 geçerlidir, daha sonraki sürümlere uygulanmaz.  
  
 .NET Framework sürüm 1.0 ve 1.1, kodunuzun diğer derlemeler için kullanılamaz olduğunu onaylama tür sistem erişilebilirliği'bir nuance farkında olmanız gerekir. Bildirilen bir yöntemi **sanal** ve **iç** (**aşırı geçersiz kılınabilir arkadaş** Visual Basic'te) üst sınıfın vtable girişi geçersiz kılabilir ve yalnızca kullanılabilir aynı bütünleştirilmiş kod içinde iç olduğundan. Ancak, geçersiz kılmak için erişilebilirlik tarafından belirlenen **sanal** anahtar sözcüğü ve kod sınıfı erişiminin olduğu sürece başka bir bütünleştirilmiş koddan kılınmasına oluşabilir. Bir geçersiz kılma olası bir sorunu sunarsa, düzeltin veya kaldırmak için bildirime dayalı güvenlik kullanın **sanal** kati şekilde gerekli değilse, anahtar sözcüğü.  
  
 Bir dil derleyicisi bir derleme hatası ile bu geçersiz kılmaları engelliyor olsa bile, bunu geçersiz kılmak için diğer derleyicilerle yazılan kod mümkün olduğuna dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
