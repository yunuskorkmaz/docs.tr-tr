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
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181151"
---
# <a name="securing-method-access"></a>Yöntem Erişiminin Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bazı yöntemler, rasgele güvenilmeyen kodun çağrılmasını sağlamak için uygun olmayabilir. Bu tür yöntemler çeşitli riskler oluşturmaktadır: Yöntem bazı sınırlı bilgiler sağlayabilir; ona aktarılan herhangi bir bilginin olduğuna inanabilir; parametreleri üzerinde hata denetimi yapmayabilir; veya yanlış parametrelerle arızalanabilir veya zararlı bir şey yapabilir. Bu durumların farkında olmalı ve yöntemi korumaya yardımcı olmak için harekete geçmelisiniz.  
  
 Bazı durumlarda, genel kullanıma yönelik olmayan ancak yine de herkese açık olması gereken yöntemleri kısıtlamanız gerekebilir. Örneğin, kendi DL'leriniz arasında çağrılması gereken bir arabiriminiz olabilir ve bu nedenle herkese açık olması gerekir, ancak müşterilerin kullanmasını önlemek veya kötü amaçlı kodun bileşeninize giriş noktasını kullanmasını önlemek için bu arabirimi herkese açık hale getirmek istemezsiniz. Genel kullanım için tasarlanmamış bir yöntemi kısıtlamak için başka bir yaygın neden (ancak ortak olmalıdır) belgelemek ve çok iç arabirim olabilir desteklemek zorunda önlemektir.  
  
 Yönetilen kod, yöntem erişimini kısıtlamanın çeşitli yollarını sunar:  
  
- Güvenilen sınıf, derleme veya türetilmiş sınıflar için erişilebilirlik kapsamını sınırlayın. Yöntem erişimini sınırlamanın en basit yolu budur. Türemiş sınıfların, bazı durumlarda üst sınıfın kimliğini paylaşmalarına rağmen, türedikleri sınıfların türetildiği sınıftan daha az güvenilir olabileceğini unutmayın. Özellikle, güvenlik bağlamında mutlaka kullanılmayan **korumalı**anahtar kelimeden güven çıkarmayın.  
  
- Yöntem erişimini belirli bir kimliği arayanlarla (temelde, seçtiğiniz belirli [bir kanıt,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) yayımcı, bölge vb.) sınırlandırın.  
  
- Yöntem erişimini, seçtiğiniz izinlere sahip olan arayanlarla sınırlandırın.  
  
 Benzer şekilde, bildirimsel güvenlik sınıfların devralma denetlemek için izin verir. Aşağıdakileri yapmak için **InheritanceDemand'ı** kullanabilirsiniz:  
  
- Türetilen sınıfların belirli bir kimliğe veya izne sahip olmasını zorunlu kılmasını zorunlu kınla.  
  
- Belirli bir kimliğe veya izine sahip olmak için belirli yöntemleri geçersiz kılan türemiş sınıflar gerektirir.  
  
 Aşağıdaki örnek, arayanların belirli bir güçlü adla imzalanmasını gerekterek, sınırlı erişim için ortak bir sınıfın korunmasına nasıl yardımcı olabileceğini gösterir. Bu örnek, <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> güçlü ad için bir **Talep** ile kullanır. Güçlü bir ada sahip bir derlemenin nasıl imzalatılılabildiğini anlatan görev tabanlı bilgiler için [bkz.](../../standard/assembly/create-use-strong-named.md)  
  
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
 Belirli sınıfların ve yöntemlerin yanı sıra özelliklerin ve olayların kısmen güvenilen kodtarafından kullanılmasını önlemek için bu bölümde gösterilen bildirimleri kullanın. Bu bildirimleri bir sınıfa uygulayarak, korumayı tüm yöntemlerine, özelliklerine ve olaylarına uygularsınız; ancak, alan erişiminin bildirimsel güvenliktarafından etkilenmediğini unutmayın. Ayrıca, bağlantı taleplerinin yalnızca acil arayanlara karşı korunmaya yardımcı olduğunu ve yine de cezbetme saldırılarına maruz kabileceğini unutmayın.  
  
> [!NOTE]
> .NET Framework 4'te yeni bir şeffaflık modeli tanıtıldı. [Güvenlik-Saydam Kod, Düzey 2](security-transparent-code-level-2.md) modeli öznitelik ile <xref:System.Security.SecurityCriticalAttribute> güvenli kodu tanımlar. Güvenlik açısından kritik kod, hem arayanların hem de devralanların tam olarak güvenilmesini gerektirir. Önceki .NET Framework sürümlerinden kod erişim güvenlik kuralları altında çalışan derlemeler düzey 2 derlemelerini çağırabilir. Bu durumda, güvenlik açısından kritik öznitelikler tam güven için bağlantı talepleri olarak kabul edilecektir.  
  
 Güçlü adlandırılmış derlemelerde, [bir LinkDemand,](link-demands.md) bunların kullanımını tam olarak güvenilen arayanlara kısıtlamak için tüm genel olarak erişilebilen yöntemlere, özelliklere ve olaylara uygulanır. Bu özelliği devre dışı kalmak <xref:System.Security.AllowPartiallyTrustedCallersAttribute> için özniteliği uygulamanız gerekir. Bu nedenle, güvenilmeyen arayanları hariç tutmak için sınıfları açıkça işaretlemeyalnızca bu özniteliğe sahip imzalanmamış derlemeler veya derlemeler için gereklidir; bu bildirimleri, güvenilmeyen arayanlar için tasarlanmayan türlerin bir alt kümesini işaretlemek için kullanabilirsiniz.  
  
 Aşağıdaki örnekler, sınıfların ve üyelerin güvenilmeyen kod tarafından kullanılmasını nasıl önleyeceğinizi gösterir.  
  
 Kamu mühürsüz sınıflar için:  
  
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
  
 Kamu mühürlü sınıflar için:  
  
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
  
 Taban sınıfın tam güven gerektirmediği genel geçersiz kılma işlevleri için:  
  
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
  
 Taban sınıfın tam güven gerektirdiği genel geçersiz kılma işlevleri için:  
  
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
> Bu bölüm, bir yöntemi hem `virtual` de `internal` (Visual`Overloads` `Overridable` `Friend` Basic'te) olarak bildirirken bir güvenlik sorunu hakkında uyarır. Bu uyarı yalnızca .NET Framework sürümleri 1.0 ve 1.1 için geçerlidir, sonraki sürümler için geçerli değildir.  
  
 .NET Framework sürümleri 1.0 ve 1.1'de, kodunuzu diğer derlemeler tarafından kullanılamıyorsa onaylarken tür sistemi erişilebilirliğinin bir nüansını fark etmeniz gerekir. **Sanal** ve **dahili** olarak bildirilen bir yöntem (Visual Basic'te**Overridable Friend Overloads)** üst sınıfın vtable girişini geçersiz kılabilir ve yalnızca aynı derleme nin içinden kullanılabilir, çünkü dahilidir. Ancak, geçersiz kılma için erişilebilirlik **sanal** anahtar kelime tarafından belirlenir ve bu kod sınıfın kendisine erişimi olduğu sürece başka bir derleme geçersiz kılınabilir. Geçersiz kılma olasılığı bir sorun teşkil ediyorsa, bunu düzeltmek için bildirimsel güvenliği kullanın veya kesinlikle gerekli değilse **sanal** anahtar sözcüğü kaldırın.  
  
 Bir dil derleyicisi bir derleme hatası ile bu geçersiz kılmaları önlerse bile, diğer derleyicilerle yazılmış kodun geçersiz kılınmasını mümkün olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
