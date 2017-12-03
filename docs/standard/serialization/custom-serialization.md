---
title: "Özel seri hale getirme"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e85ee15223bc135384d698a175d57b4fd543747
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-serialization"></a>Özel seri hale getirme
Özel serileştirme seri hale getirme ve seri durumdan çıkarma türü denetleme işlemidir. Seri hale getirme denetleyerek, seri hale getirmek ve seri durumdan türü çekirdek işlevselliğini çiğnemekten olmadan bir türü sürümleri arasında özelliği seri hale getirme uyumluluğundan emin olmak mümkündür. Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan. Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir. Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir. Aşağıdaki bölümlerde serileştirme denetleme açıklanmaktadır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  .NET Framework 4.0 önceki sürümlerde, kısmen güvenilir bir derleme özel kullanıcı verilerini serileştirmek GetObjectData kullanarak gerçekleştirilmiştir. Yöntem ile işaretlenmiş sürüm 4.0 başlayarak <xref:System.Security.SecurityCriticalAttribute> , kısmen güvenilir derlemeler yürütmeyi engelleyen özniteliği. Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Çalışmakta olan özel yöntemler sırasında ve sonrasında seri hale getirme  
 En iyi uygulama ve en kolay yolu (.NET Framework 2.0 sürümünde sunulan) olan aşağıdaki öznitelikler veri sırasında ve sonrasında serileştirme düzeltmek için kullanılan yöntemleri uygulamak için:  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Özniteliklerden herhangi birinin veya tüm dört aşamaları seri hale getirme ve seri durumdan çıkarma işlemleri katılmayı türüne izin verme. Öznitelikleri her aşaması sırasında çağrılması gereken türü yöntemleri belirtin. Yöntem serileştirme akış erişmemesi ancak bunun yerine önce ve seri hale getirme, veya önce ve sonra seri durumdan çıkarma nesnesi alter izin verir. Öznitelikleri türü Devralma Hiyerarşisi tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide taban en çok türetilen çağrılır. Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi. Ayrıca, bu mekanizma alanları ve seri hale getirme akış alımı popülasyonunu yoksaymak biçimlendiricileri sağlar. Ayrıntılar ve seri hale getirme ve seri durumdan çıkarma denetleme örnekleri için önceki bağlantılardan birini tıklatın.  
  
 Ayrıca, yeni bir alan için mevcut bir seri hale getirilebilir türü eklerken, uygulama <xref:System.Runtime.Serialization.OptionalFieldAttribute> alana özniteliği. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yeni alan eksik bir akış işlendiğinde alan yokluğu yok sayar.  
  
## <a name="implementing-the-iserializable-interface"></a>ISerializable arabirimi uygulama  
 Seri hale getirme denetlemek için diğer bir yol uygulayarak elde edilen <xref:System.Runtime.Serialization.ISerializable> bir nesne üzerinde arabirimi. Ancak, önceki bölümde yöntemi denetim serileştirme için bu yöntem yerini aldığını unutmayın.  
  
 Ayrıca, varsayılan seri hale getirme ile işaretli bir sınıfını kullanmamalısınız [Serializable](xref:System.SerializableAttribute) özniteliği ve bildirim temelli veya kesinlik temelli güvenliği sınıf düzeyinde veya kendi oluşturucular sahiptir. Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
 Uygulama <xref:System.Runtime.Serialization.ISerializable> uygulama içerir `GetObjectData` yöntemi ve nesnenin seri durumda olduğunda kullanan bir özel Oluşturucu. Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.  
  
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
[SecurityPermissionAttribute(SecurityAction.Demand,   
SerializationFormatter =true)]  
  
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
  
    Protected Sub New(ByVal info As SerializationInfo, _  
    ByVal context As StreamingContext)   
        n1 = info.GetInt32("i")  
        n2 = info.GetInt32("j")  
        str = info.GetString("k")  
    End Sub 'New  
  
    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Public Overridable Sub GetObjectData(ByVal info As _  
    SerializationInfo, ByVal context As StreamingContext)   
        info.AddValue("i", n1)  
        info.AddValue("j", n2)  
        info.AddValue("k", str)  
    End Sub   
End Class  
```  
  
 Zaman **GetObjectData** çağrılır doldurmak için sorumlu seri hale getirme sırasında <xref:System.Runtime.Serialization.SerializationInfo> yöntemi çağrısı ile sağlanan. Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin. Herhangi bir metin adı olarak kullanılabilir. Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla. Türetilen sınıflar çağrısı **GetObjectData** temel nesnesi üzerinde yöntemi, ikinci uygular <xref:System.Runtime.Serialization.ISerializable>.  
  
 Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın. Bu nedenle, serileştirme gerçekleştirir kodu gerektirir [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilmiş. Varsayılan ilkesi altında için Internet indirilen bu izni verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir. **GetObjectData** yöntemi açıkça korunmalıdır ya da göre yoğun [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> göre özellikle yardımcı diğer izinler yoğun ya da belirtilen bayrağı özel verileri korur.  
  
 Özel bir alan gizli bilgileri depoluyorsa, üzerinde uygun izinleri talep **GetObjectData** verileri korumak için. Verildi bu kodu unutmayın [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile **SerializationFormatter** bayrağı belirtilmiş görüntüleyebilir ve özel alanlarında depolanan verilerin değiştirebilirsiniz. Bu kötü amaçlı çağıran verilen [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gizli dizin konumları veya izin verilenler gibi verileri görüntüleyebilir ve bilgisayardaki güvenlik açığından verileri kullanın. Güvenlik izni bayrakları belirtebilirsiniz tam bir listesi için bkz: [SecurityPermissionFlag numaralandırma](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Zaman stres önemlidir <xref:System.Runtime.Serialization.ISerializable> her ikisi de uygulanmalı bir sınıfa eklenen **GetObjectData** ve özel Oluşturucu. Derleyici, sizi uyarır **GetObjectData** eksik. Ancak, bir oluşturucu uyarlamasını gerçekleştirmek imkansız olduğu için hiçbir uyarı oluşturucusu yok ve sınıf oluşturucu olmadan serisini kaldırmak için bir girişimde zaman bir özel durum için sağlanır.  
  
 Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi. Örneğin, bir `SetObjectData` yöntemi bir arabirim bir parçası olarak tanımlanmışsa ortak olmalıdır; böylece kullanıcıların sahip karşı korumak için kod yazmanız gerekir **SetObjectData** yöntemi birden çok kez çağrıldı. Aksi takdirde, kötü amaçlı bir uygulama, çağıran **SetObjectData** yöntemi bir işlem yürütme sürecinde bir nesne üzerinde olası sorunlara neden olabilir.  
  
 Seri durumdan çıkarma sırasında <xref:System.Runtime.Serialization.SerializationInfo> bu amaç için sağlanan Oluşturucusu kullanılarak sınıfı geçirilir. Nesnenin seri durumda olduğunda Oluşturucu yerleştirilen tüm görünürlük kısıtlamaları göz ardı edilir; Bu nedenle sınıf ortak, korumalı, iç veya özel olarak işaretleyebilirsiniz. Ancak, sınıf; bu durumda Oluşturucusu özel işaretlenmelidir korumalı olduğu sürece korumalı Oluşturucusu yapmak en iyi uygulamadır. Oluşturucusu de kapsamlı giriş doğrulaması gerçekleştirmeniz gerekir. Kötü amaçlı kod tarafından kötüye kullanımı önlemek için aynı güvenlik denetimleri ve diğer oluşturucuyu kullanarak sınıfının bir örneği elde etmek için gereken izinler Oluşturucusu uygulamalıdır. Bu öneriyi uygulamazsanız kötü amaçlı kod bir nesne preserialize, denetimi ile elde [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilen ve nesnedeki atlayarak herhangi bir istemci bilgisayarda Standart örnek oluşturma sırasında bir public oluşturucuya kullanarak uygulanmış güvenliği.  
  
 Nesnenin durumunu geri yüklemek için yalnızca değişkenlerin değerleri almak <xref:System.Runtime.Serialization.SerializationInfo> seri hale getirme sırasında kullanılan adları kullanarak. Taban sınıfı uyguluyorsa <xref:System.Runtime.Serialization.ISerializable>, temel oluşturucuyu değişkenlerini geri yüklemek temel nesne izin vermek için çağrılmalıdır.  
  
 Ne zaman, türetilen yeni bir sınıf uygulayan bir <xref:System.Runtime.Serialization.ISerializable>, türetilen sınıfın iki Oluşturucusu uygulamalıdır yanı sıra **GetObjectData** serileştirilmesi gereken değişkenleri varsa yöntemi. Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.  
  
```csharp  
[Serializable]  
public class ObjectTwo : MyObject  
{  
    public int num;  
  
    public ObjectTwo() : base()  
    {  
    }  
  
    protected ObjectTwo(SerializationInfo si,   
    StreamingContext context) : base(si,context)  
    {  
        num = si.GetInt32("num");  
    }  
[SecurityPermissionAttribute(SecurityAction.Demand,  
SerializationFormatter = true)]  
    public override void GetObjectData(SerializationInfo si,   
    StreamingContext context)  
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
  
    <SecurityPermissionAttribute(SecurityAction.Demand, _  
    SerializationFormatter := True)>  _  
    Public Overrides Sub GetObjectData(ByVal si As _  
    SerializationInfo, ByVal context As StreamingContext)   
        MyBase.GetObjectData(si, context)  
        si.AddValue("num", num)      
    End Sub   
End Class  
```  
  
 Seri durumdan çıkarma Oluşturucusu çağrı temel sınıfı unutmayın. Bu yapılır değil, temel sınıf oluşturucu hiçbir zaman denir ve nesne tamamen seri durumdan çıkarma sonra oluşturulan değil.  
  
 Nesneleri, içinden yeniden; ve çağrılan yöntemler çağrıyı yapan zaman serisi değil nesne başvuruları başvurmak çünkü seri durumdan çıkarma sırasında çağıran yöntemleri istenmeyen yan etkileri olabilir. Sınıf olan Implements çıkarıldıysa <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> yöntemi tüm nesne grafiğinin seri durumdan olduğunda otomatik olarak çağrılır. Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi. Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir. Seri durumdan çıkarma sırasında anahtar ve değer çiftleri almak kolaydır, ancak bu nesneleri geri karma tablosu için sorunlara neden olabilir karma tablosundan türetilmiş bu sınıfları garanti olduğundan ekleme seri durumdan. Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İkili seri hale getirme](binary-serialization.md)  
 [XML ve SOAP seri hale getirme](xml-and-soap-serialization.md)  
 [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
