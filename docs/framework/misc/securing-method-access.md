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
ms.openlocfilehash: e981d75ead5ec2e7f95a854da8c0fa42f476d9da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910784"
---
# <a name="securing-method-access"></a>Yöntem Erişiminin Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bazı yöntemler rastgele güvenilmeyen kodun çağrısına izin vermek için uygun olmayabilir. Bu tür yöntemler çeşitli riskler oluşturmaktadır: Yöntem bazı kısıtlı bilgiler sağlayabilir; Bu, kendisine geçirilen bilgilere benzeyebilir; parametrelerde hata denetimi yapamayabilir; ya da yanlış parametrelerle hatalı olabilir veya zararlı bir şey olabilir. Bu durumları bilmeniz ve yöntemi korumanıza yardımcı olması için işlem yapmanız gerekir.  
  
 Bazı durumlarda, genel kullanım için tasarlanmamış ancak hala genel olması gereken yöntemleri kısıtlamanız gerekebilir. Örneğin, kendi dll 'larınız genelinde çağrılması gereken bir arayüze sahip olabilirsiniz ve bu nedenle genel olması gerekir, ancak müşterilerin bunu kullanmasını engellemek veya kötü amaçlı kodun giriş noktasını bileşeninize kötüye kullanmasını engellemek için genel kullanıma sunmak istemezsiniz. Bir yöntemi genel kullanıma yönelik amaçlanmayan (ancak genel olması gerekir) bir diğer yaygın neden, çok dahili bir arabirim olabileceğini belgelemek ve desteklemek zorunda kalmamak.  
  
 Yönetilen kod, yöntem erişimini kısıtlamak için çeşitli yollar sunar:  
  
- Güveniliyorsa, erişilebilirlik kapsamını sınıf, derleme veya türetilmiş sınıflarla sınırlayın. Bu yöntem erişimini sınırlamanın en kolay yoludur. Genel olarak, türetilmiş sınıfların türettikleri sınıftan daha az güvenilir olabileceğini, ancak bazı durumlarda üst sınıfın kimliğini paylaştıkları unutulmamalıdır. Özellikle, güvenlik bağlamında kullanılması gerekmeyen, **korunan**anahtar kelimeden güven çıkarmayın.  
  
- Belirli bir kimliğin çağıranlarını (Aslýnda, The The Strong Name, Publisher, Zone [](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) vb.) ve seçtiğiniz bir kimliğe ait çağıranlara erişimi sınırlayın.  
  
- Seçtiğiniz izinlere sahip çağıranlara erişim yöntemini sınırlayın.  
  
 Benzer şekilde, bildirime dayalı güvenlik, sınıfların devralınmasını denetlemenize olanak tanır. **InheritanceDemand** kullanarak şunları yapabilirsiniz:  
  
- Türetilmiş sınıfların belirtilen kimliğe veya izne sahip olmasını gerektir.  
  
- Belirli bir kimliğe veya izne sahip olacak şekilde belirli yöntemleri geçersiz kılan türetilmiş sınıflar gerektir.  
  
 Aşağıdaki örnek, çağıranların belirli bir tanımlayıcı ad ile imzalandığından emin olmak için genel bir sınıfı sınırlı erişim için nasıl koruyabileceğinizi gösterir. Bu örnek, <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> öğesini tanımlayıcı ad için bir **talep** ile kullanır. Bir derlemeyi güçlü bir adla imzalama hakkında görev tabanlı bilgiler için, bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Belirli sınıfların ve yöntemlerin yanı sıra özellik ve olayların kısmen güvenilen kod tarafından kullanılmasını engellemek için bu bölümde gösterilen bildirimleri kullanın. Bu bildirimleri bir sınıfa uygulayarak, korumayı tüm yöntemlerine, özelliklerine ve olaylarına uygularsınız; Ancak, alan erişiminin bildirime dayalı güvenlik tarafından etkilenmediğini unutmayın. Ayrıca, bağlantı taleplerini yalnızca anında çağıranlara karşı korumaya yardımcı olur ve yine de söz konusu saldırı saldırılarına maruz kalabilir.  
  
> [!NOTE]
> .NET Framework 4 ' te yeni bir saydamlık modeli sunuldu. [Güvenlik açısından saydam kod, düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modeli, güvenli kodu <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle tanımlar. Güvenlik açısından kritik kod, çağıranların ve herıtors 'ın tamamen güvenilir olmasını gerektirir. Önceki .NET Framework sürümlerinden kod erişimi güvenlik kuralları altında çalışan derlemeler, düzey 2 derlemelerini çağırabilir. Bu durumda, güvenlik açısından kritik öznitelikler tam güven için bağlantı talepleri olarak kabul edilir.  
  
 Tanımlayıcı adlı derlemelerde, bir [LinkDemand](../../../docs/framework/misc/link-demands.md) , kullanımlarını tam güvenilir çağıranlar olarak kısıtlamak için genel olarak erişilebilen tüm yöntemlere, özelliklere ve olaylara uygulanır. Bu özelliği devre dışı bırakmak için <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği uygulamanız gerekir. Bu nedenle, güvenilmeyen çağıranları hariç tutmak için sınıfları açıkça işaretlemek yalnızca imzasız derlemeler veya bu özniteliğe sahip derlemeler için gereklidir; Bu bildirimleri, güvenilmeyen çağıranlar için tasarlanmamış bir tür alt kümesini işaretlemek için kullanabilirsiniz.  
  
 Aşağıdaki örneklerde, sınıfların ve üyelerin güvenilmeyen kod tarafından nasıl kullanılacağı gösterilmektedir.  
  
 Genel korumalı olmayan sınıflar için:  
  
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
  
 Genel korumalı sınıflar için:  
  
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
  
 Genel geçersiz kılma işlevleri için, taban sınıfının tam güven talep etmez:  
  
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
  
 Temel sınıfın tam güven talep ettiği genel geçersiz kılma işlevleri için:  
  
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
  
 Ortak arabirimler için:  
  
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
> `virtual` Bu bölüm, `internal` bir yöntemi hem hem de (`Overloads` `Overridable` `Friend` Visual Basic olarak) bildirirken bir güvenlik sorunuyla ilgili olarak uyarır. Bu uyarı yalnızca 1,0 ve 1,1 .NET Framework sürümleri için geçerlidir, sonraki sürümler için geçerli değildir.  
  
 .NET Framework sürüm 1,0 ve 1,1 ' de, kodunuzun diğer derlemeler için kullanılamadığını onaylayarak sistem erişilebilirliği türünün farkında olmanız gerekir. **Sanal** ve **iç** olarak belirtilen bir Yöntem (Visual Basic**geçersiz kılınabilir arkadaş aşırı yüklemeleri** ) üst sınıfın vtable girdisini geçersiz kılabilir ve yalnızca aynı bütünleştirilmiş kod içinden kullanılabilir çünkü iç. Ancak, geçersiz kılma için erişilebilirlik, **sanal** anahtar sözcüğü tarafından belirlenir ve bu kod, sınıfın kendine erişimi olduğu sürece başka bir derlemeden geçersiz kılınabilir. Geçersiz kılma olasılığı bir sorun sunduğunda, sorunu gidermek için bildirime dayalı güvenlik kullanın ya da kesinlikle gerekmiyorsa **sanal** anahtar sözcüğünü kaldırın.  
  
 Bir dil derleyicisi bu geçersiz kılmaları derleme hatası ile engelseler de, diğer derleyicilerle yazılmış kodların geçersiz kılınmasına olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
