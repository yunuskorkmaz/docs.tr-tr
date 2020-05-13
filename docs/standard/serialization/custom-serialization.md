---
title: Özel serileştirme
description: Özel serileştirme, bir türün serileştirme ve serisini kaldırma işlemi denetliyor. Serileştirme denetimi serileştirme uyumluluğuna emin olabilir.
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
ms.openlocfilehash: dcd5fa2777d2f1e351179570806a95eb835ad843
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376001"
---
# <a name="custom-serialization"></a>Özel serileştirme
Özel serileştirme, bir türün serileştirme ve serisini kaldırma işlemidir. Serileştirme ' i denetleyerek, bir türün sürümleri arasında serileştirme ve seri durumdan çıkarma özelliği olan serileştirme uyumluluğunu sağlamak mümkündür. Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan. Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir. Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir. Aşağıdaki bölümlerde serileştirme denetiminin nasıl yapılacağı açıklanır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> .NET Framework 4,0 ' den önceki sürümlerde, kısmen güvenilen bir derlemede özel kullanıcı verilerinin serileştirilmesi, GetObjectData kullanılarak gerçekleştirildi. Sürüm 4,0 ' den başlayarak, bu yöntem <xref:System.Security.SecurityCriticalAttribute> kısmen güvenilen derlemelerde yürütmeyi önleyen özniteliğiyle işaretlenir. Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Serileştirme sırasında ve sonrasında özel yöntemler çalıştırma  
 En iyi yöntem ve en kolay yolu (.NET Framework sürüm 2,0 ' de kullanıma sunulmuştur), serileştirme sırasında ve sonrasında verileri düzeltmek için kullanılan yöntemlere aşağıdaki öznitelikleri uygular:  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Bu öznitelikler, tür serileştirme ve seri durumdan çıkarma işlemlerinin herhangi birine veya tüm dört aşamaya katılmasına izin verir. Öznitelikler, her aşamada çağrılması gereken türün yöntemlerini belirler. Yöntemler serileştirme akışına erişemez ancak bunun yerine, serileştirme veya sonrasında nesneyi, Serileştirmeden önce ve sonra ve serisini kaldırmadan önce ve sonra değiştirmeniz sağlar. Öznitelikler, tür devralma hiyerarşisinin tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide temel alınan en fazla türetilmiş öğesine çağrılır. Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi. Buna ek olarak, bu mekanizma, Biçimlendiriciler 'nın alanların ve seri hale getirme akışından alımı yok saymasına izin verir. Serileştirme ve seri durumdan çıkarmayı denetleme ayrıntıları ve örnekleri için önceki bağlantılardan herhangi birine tıklayın.  
  
 Ayrıca, var olan bir serileştirilebilir türe yeni bir alan eklerken, bu <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliği alana uygulayın. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Ve, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Yeni alan eksik bir akış işlendiği zaman alanın yokluğunu yoksayar.  
  
## <a name="implementing-the-iserializable-interface"></a>ISerializable arabirimini uygulama  
 Serileştirme denetiminin diğer yolu, <xref:System.Runtime.Serialization.ISerializable> bir nesne üzerinde arabirimini uygulayarak elde edilir. Ancak, önceki bölümdeki yöntemin serileştirme denetlemek için bu yöntemin yerini almıştır.  
  
 Ayrıca, [seri hale getirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenmiş bir sınıfta varsayılan serileştirme kullanmamalısınız ve sınıf düzeyinde ya da oluşturucuları üzerinde bildirim veya kesinlik güvenliği vardır. Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
 Uygulama <xref:System.Runtime.Serialization.ISerializable> , `GetObjectData` yöntemi ve nesne seri durumdan çıkarıldığınızda kullanılan özel bir oluşturucuyu uygulamayı içerir. Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.  
  
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
  
 Serileştirme işlemi sırasında **GetObjectData** çağrıldığında, <xref:System.Runtime.Serialization.SerializationInfo> verilen yöntemi çağrı ile doldurmaktan siz sorumlusunuz. Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin. Herhangi bir metin adı olarak kullanılabilir. Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla. Türetilmiş sınıflar, ikinci uygularsa, temel nesnede **GetObjectData** yöntemini çağırmalıdır <xref:System.Runtime.Serialization.ISerializable> .  
  
 Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın. Bu nedenle, serileştirme gerçekleştiren kod, belirtilen bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> . Varsayılan ilke altında, bu izin Internet 'Ten indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir. **GetObjectData** yöntemi, [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> belirtilen bayrağıyla veya özellikle özel verileri korumaya yardımcı olan diğer Izinler için gerekli olan SecurityPermission 'ı kesin olarak korumalı olmalıdır.  
  
 Özel bir alan gizli bilgileri depoluyorsa, verileri korumak için **GetObjectData** üzerinde uygun izinleri talep etmelisiniz. Belirtilen **SerializationFormatter** bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) verilen kodun özel alanlarda depolanan verileri görüntüleyip değiştireabileceğini unutmayın. Bu [SecurityPermission izni](xref:System.Security.Permissions.SecurityPermissionAttribute) verilen kötü niyetli bir çağıran, gizli dizin konumları gibi verileri görüntüleyebilir veya izinler verebilir ve bilgisayardaki bir güvenlik açığından yararlanmak için verileri kullanabilir. Belirtebileceğiniz güvenlik izni bayraklarının tüm listesi için bkz. [SecurityPermissionFlag numaralandırması](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 <xref:System.Runtime.Serialization.ISerializable>Bir sınıfa eklendiğinde, hem **GetObjectData** hem de özel oluşturucuyu uygulamanız gerektiğini belirten bir stres olması önemlidir. **GetObjectData** eksik olduğunda derleyici sizi uyarır. Ancak, bir oluşturucunun uygulanmasını zorlamak imkansız olduğundan, Oluşturucu yoksa bir uyarı sağlanmaz ve bir sınıfın Oluşturucusu olmadan serisini kaldırma girişimi yapıldığında bir özel durum oluşturulur.  
  
 Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi. Örneğin, bir `SetObjectData` Yöntem bir arabirimin parçası olarak tanımlanmışsa ortak olmalıdır; bu nedenle kullanıcıların, **SetObjectData** yönteminin birden çok kez çağrıldığından savunmak için kod yazması gerekir. Aksi halde, bir işlemi yürütme işlemindeki bir nesne üzerinde **SetObjectData** yöntemini çağıran kötü amaçlı bir uygulama olası sorunlara neden olabilir.  
  
 Seri durumdan çıkarma sırasında, <xref:System.Runtime.Serialization.SerializationInfo> Bu amaçla verilen Oluşturucu kullanılarak sınıfa geçirilir. Oluşturucuya yerleştirilmiş tüm Görünürlük kısıtlamaları, nesne seri durumdan çıkarıldığı zaman yok sayılır; Bu nedenle, sınıfı ortak, korumalı, iç veya özel olarak işaretleyebilirsiniz. Ancak, sınıf mühürlenmedikçe oluşturucunun korunmasını sağlamak en iyi uygulamadır, bu durumda oluşturucunun özel olarak işaretlenmesi gerekir. Oluşturucu Ayrıca kapsamlı giriş doğrulaması da gerçekleştirmelidir. Kötü amaçlı kodun kötüye kullanılmasına engel olmak için, Oluşturucu, başka bir Oluşturucu kullanarak sınıfın bir örneğini almak için gereken güvenlik denetimlerini ve izinlerini zorunlu kılmaz. Bu öneriyi izlemeden, kötü amaçlı kod bir nesneyi önceden serileştirme, belirtilen bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile denetim elde edebilir <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> ve bir ortak Oluşturucu kullanılarak standart örnek oluşturma sırasında uygulanan güvenliği atlayarak bir istemci bilgisayardaki nesne serisini kaldıramıyor.  
  
 Nesnenin durumunu geri yüklemek için, <xref:System.Runtime.Serialization.SerializationInfo> serileştirme sırasında kullanılan adları kullanarak değişkenlerin değerlerini almanız yeterlidir. Temel sınıf uygularsa <xref:System.Runtime.Serialization.ISerializable> , temel oluşturucunun değişkenlerini geri yüklemelerine izin vermek için temel Oluşturucu çağrılmalıdır.  
  
 Uygulamadan yeni bir sınıf türettiğinizde <xref:System.Runtime.Serialization.ISerializable> , türetilmiş sınıf, serileştirilmesi gereken değişkenlere sahipse, hem oluşturucuyu hem de **GetObjectData** metodunu uygulamalıdır. Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.  
  
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
  
 Seri kaldırma oluşturucusunda temel sınıfı çağırmayı unutmayın. Bu yapılmazsa, temel sınıftaki Oluşturucu hiçbir şekilde çağrılmaz ve nesne seri durumdan çıktıktan sonra tam olarak oluşturulmamış olur.  
  
 Nesneler, iç içe içinden yeniden yapılandırılır; ve öğesini kaldırma sırasında çağırma yöntemleri istenmeyen yan etkilere sahip olabilir, çünkü çağrılan yöntemler, Çağrının yapıldığı zaman serisi kaldırılan nesne başvurularına başvurabilir. Seri durumdan çıkarılan sınıf öğesini uygularsa, <xref:System.Runtime.Serialization.IDeserializationCallback> <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> nesne grafiğinin tamamı seri durumdan çıkarılmışsa yöntem otomatik olarak çağrılır. Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi. Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir. Seri durumdan çıkarma sırasında anahtar ve değer çiftlerini almak kolaydır, ancak karma tablodan türetilmiş sınıfların seri durumdan çıkarıldığından emin olmadığı için bu nesneleri karma tabloya geri eklemek sorunlara yol açabilir. Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
- [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
