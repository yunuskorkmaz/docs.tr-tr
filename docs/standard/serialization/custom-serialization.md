---
title: Özel serileştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 83538dc971419ad7918c16c5ccbd2003d16e2c6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931748"
---
# <a name="custom-serialization"></a>Özel serileştirme
Özel seri hale getirme serileştirme ve seri durumundan çıkarma bir türün denetleme işlemidir. Serileştirme denetleyerek, türü çekirdek işlevselliğini bozucu olmayan bir tür sürümleri arasında seri hale getrime ve yeteneği olan serileştirme uyumluluğu sağlamak mümkündür. Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan. Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir. Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir. Aşağıdaki bölümler serileştirme denetlemek nasıl açıklar.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  .NET Framework 4.0 önceki sürümlerinde, özel kullanıcı veri kısmen güvenilen bir derleme serileştirme GetObjectData kullanarak gerçekleştirilebilir. Yöntem ile işaretlenmiş bir sürüm 4.0, başlayarak <xref:System.Security.SecurityCriticalAttribute> kısmen güvenilen derlemelerde yürütme önleyen özniteliği. Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Özel yöntemlerini sırasında ve sonra serileştirme çalıştıran  
 En iyi yöntem ve (.NET Framework'ün 2.0 sürümünde sunulan) kolay yolu olan aşağıdaki öznitelikler sırasında ve seri hale getirme sonra veri düzeltmek için kullanılan yöntemleri uygulamak için:  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Bu öznitelikler herhangi birinin veya tüm dört serileştirme ve seri durumundan çıkarma işlemlerinin aşamadan katılmak türüne izin verin. Öznitelikleri yöntemleri her aşamada çağrılmalıdır türü belirtin. Yöntemleri seri hale getirme akışı erişim değil ancak bunun yerine nesne önce ve seri hale getirme, veya önce ve sonra seri durumundan çıkarma alter izin. Öznitelikleri türü devralma hiyerarşisinin tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide temel en türetilen çağrılır. Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi. Ayrıca, bu mekanizma alanları ve seri hale getirme akışı almanın popülasyonu yok sayılacak biçimlendiricileri sağlar. Ayrıntıları ve örnekleri serileştirme ve seri durumundan çıkarma denetlemek için önceki bağlantılardan herhangi birine tıklayın.  
  
 Ayrıca, yeni bir alan varolan serializable bir tür eklerken uygulamak <xref:System.Runtime.Serialization.OptionalFieldAttribute> alanına öznitelik. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yeni alan eksik olan bir akış işlendiğinde alan olmaması yok sayar.  
  
## <a name="implementing-the-iserializable-interface"></a>ISerializable arabirimini uygulayan  
 Serileştirme denetlemek için başka bir şekilde uygulayarak sağlanır <xref:System.Runtime.Serialization.ISerializable> arabirimdeki bir nesne. Ancak, önceki bölümde yöntem Denetim serileştirme için bu yöntem yerine geçer unutmayın.  
  
 Ayrıca, varsayılan seri hale getirme ile işaretlenmiş bir sınıfındaki kullanmamalısınız [Serializable](xref:System.SerializableAttribute) öznitelik ve bildirim temelli veya kesinlik temelli güvenlik sınıf düzeyinde veya kendi oluşturucular sahiptir. Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
 Uygulama <xref:System.Runtime.Serialization.ISerializable> uygulayan içerir `GetObjectData` yöntemi ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu. Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 Zaman **GetObjectData** çağrılır serileştirme sırasında hesaplarla için sorumlu olduğunuz <xref:System.Runtime.Serialization.SerializationInfo> yöntem çağrısının ile sağlanan. Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin. Herhangi bir metin adı olarak kullanılabilir. Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla. Türetilen sınıfların çağrısı **GetObjectData** temel nesnesi üzerinde yöntemi, ikinci uygular <xref:System.Runtime.Serialization.ISerializable>.  
  
 Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın. Bu nedenle, serileştirme gerçekleştiren kod gerektirir [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilmiş. Varsayılan ilkesi altında çok Internet karşıdan bu izin verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir. **GetObjectData** yöntemi açıkça korunmalıdır ya da göre zorlu [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> göre özellikle yardımcı olan diğer izinler yoğun ya da belirtilen bayrağı özel verileri koruyun.  
  
 Özel bir alan duyarlı bilgi içermiyorsa, üzerinde uygun izinleri talep **GetObjectData** verileri korumak için. Verilmiş kodun [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile **SerializationFormatter** belirtilen bayrağı görüntüleyebilir ve özel alanları depolanan verileri değiştirebilirsiniz. Kötü amaçlı bir arayan bu verilen [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gizli dizin konumları veya izin verilenler gibi veri görüntüleyebilir ve bilgisayardaki güvenlik açığı verileri kullanın. Güvenlik izni bayrakları belirtebilirsiniz tam listesi için bkz. [SecurityPermissionFlag numaralandırma](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Olduğunda vurgulamak önemlidir <xref:System.Runtime.Serialization.ISerializable> için bir sınıf her ikisi de uygulanmalı eklenir **GetObjectData** ve özel Oluşturucu. Varsa derleyici sizi uyarır **GetObjectData** eksik. Ancak, bir kurucu uygulanması zorlamak olanaksız olduğundan, hiçbir uyarı oluşturucu yok ve bir sınıf oluşturucu olmadan serisini kaldırmak için girişiminde bulunulduğunda bir özel durum için sağlanır.  
  
 Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi. Örneğin, bir `SetObjectData` yöntemi bir arabirim bir parçası olarak tanımlanmışsa ortak olmalıdır; böylece kullanıcılar sahip karşı korumaya için kod yazmanız gereken **SetObjectData** yöntemi birden çok kez çağrılır. Aksi takdirde, kötü amaçlı bir uygulamayı çağırır **SetObjectData** yöntemi bir işlem yürütülürken sürecinde bir nesne üzerinde olası sorunlara neden olabilir.  
  
 Seri durumundan çıkarma sırasında <xref:System.Runtime.Serialization.SerializationInfo> bu amaç için sağlanan oluşturucu kullanılarak sınıfına geçirilen. Nesnenin seri durumda olduğunda Oluşturucu tüm görünürlük kısıtlamaları göz ardı edilir; Bu nedenle ortak, korumalı, dahili veya özel olarak sınıf işaretleyebilirsiniz. Ancak, sınıf, bu durumda oluşturucu özel işaretlenmelidir korumalı olup sürece korumalı Oluşturucu olun en iyi uygulamadır. Oluşturucuya, ayrıca kapsamlı giriş doğrulaması gerçekleştirmeniz gerekir. Kötü amaçlı kod tarafından kötüye kaçınmak için oluşturucuya aynı güvenlik denetimleri ve diğer bir oluşturucu kullanılarak sınıfının bir örneği elde etmek için gereken izinler uygulaması gerekir. Bu öneri uygulamazsanız, kötü amaçlı kod bir nesne preserialize, denetimi ile elde [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilen ve atlama herhangi bir istemci bilgisayarında bir nesneyi seri durumdan çıkarma Standart örnek oluşturma sırasında bir Genel oluşturucu kullanılarak uygulanmış güvenlik.  
  
 Nesne durumunu geri yüklemek için basitçe değişkenlerin değerlerini alma <xref:System.Runtime.Serialization.SerializationInfo> serileştirme sırasında kullanılan adları kullanarak. Temel sınıfı kullanılıyorsa <xref:System.Runtime.Serialization.ISerializable>, temel oluşturucuyu değişkenlerini geri yüklemek temel nesne izin vermek için çağrılmalıdır.  
  
 Olduğunda, türetilen yeni bir sınıf uygulayan birinden <xref:System.Runtime.Serialization.ISerializable>, türetilmiş sınıf oluşturucu her iki uygulamalıdır yanı sıra **GetObjectData** seri hale gerek değişkenleri varsa yöntemi. Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 Temel sınıfı seri durumundan çıkarma oluşturucuda çağrılacak unutmayın. Bu işlem değil, temel sınıfı Oluşturucu hiçbir zaman çağrılır ve nesne tam olarak seri durumundan çıkarma sonra oluşturulur değil.  
  
 Nesneleri içinden yeniden; ve arama yöntemleri seri durumundan çıkarma sırasında çağrılır yöntemleri için çağrı yapılır zaman serisi değil nesne başvurularını başvurabilir olduğundan istenmeyen yan etkileri olabilir. Sınıf olan uygular seri durumdan <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> yöntemi tüm nesne grafiğinin seri olduğunda otomatik olarak çağrılır. Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi. Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir. Anahtar ve değer çiftleri seri durumundan çıkarma sırasında almak kolaydır, ancak bu nesnelerine geri karma tablo sorunlara neden olabilir karma tablosundan türetilmiş bu sınıfları garanti olduğundan ekleme seri durumdan. Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
- [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
