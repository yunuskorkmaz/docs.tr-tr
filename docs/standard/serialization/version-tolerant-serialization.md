---
title: Sürüm dayanıklı serileştirme
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: 9886e2f20ef7954b01ea1f46a9eabdb9ea2cc12d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348432"
---
# <a name="version-tolerant-serialization"></a>Sürüm dayanıklı serileştirme

Sonraki uygulamaya bir sürümünden yeniden kullanılabilir olacaktır serializable türler oluşturmak sürüm 1.0 ve 1.1 .NET Framework'ün, sorunlu. Bir tür ek alanlar eklenerek değiştirilmişse, aşağıdaki sorunlar meydana gelir:

- Bir uygulamanın eski sürümleri yeni sürümleri eski türünü seri durumdan çıkarılacak sorulduğunda özel durumlar oluşturan.
- Bir uygulamanın daha yeni sürümleri, bir eksik veri türüyle eski sürümleri işlenirken özel durumlar oluşturan.

Sürüm dayanıklı serileştirme (VTS), .NET Framework 2,0 ' de sunulan ve zaman içinde seri hale getirilebilir türlerin değiştirilmesini sağlayan bir özellik kümesidir. Özellikle, VTS özellikleri, genel türler dahil olmak üzere <xref:System.SerializableAttribute> özniteliğin uygulandığı sınıflar için etkinleştirilir. VTS türü diğer sürümleriyle uyumluluk bozup olmadan bu sınıflar için yeni alanlar eklemek olanaklı kılar. Çalışan bir örnek uygulama için bkz. [Sürüm dayanıklı serileştirme teknolojisi örneği](version-tolerant-serialization-technology-sample.md).

Kullanırken VTS özelliklerin etkinleştirilip <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Ayrıca, ' yi kullanırken, fazlalık veri toleransı hariç tüm özellikler de etkinleştirilir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Serileştirme için bu sınıfları kullanma hakkında daha fazla bilgi için bkz. [Ikili serileştirme](binary-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Özellik listesi

Özellik kümesi, aşağıdakileri içerir:

- Gereksiz veya beklenmeyen verilerin toleransı. Bu türü için eski sürümleri veri göndermek için yeni bir sürümü sağlar.
- İsteğe bağlı veriler eksik tolerans. Bu yeni sürümleri için veri göndermek eski sürümleri sağlar.
- Serileştirme geri çağırmaları. Bu veri eksik olduğu durumlarda akıllı varsayılan değer ayarı sağlar.

Ayrıca, yeni bir isteğe bağlı alan eklendiğinde bildirmek için bir özellik yok. Bu, <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliğinin <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> özelliğidir.

Bu özellikler, aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınmıştır.

### <a name="tolerance-of-extraneous-or-unexpected-data"></a>Gereksiz veya beklenmeyen verilerin toleransı

Geçmişte, seri durumundan çıkarma sırasında, hiçbir gereksiz veya beklenmeyen veriler özel durum oluşturulmasına neden oldu. VTS ile aynı durumda, özel durumların oluşturulması yerine hiçbir gereksiz veya beklenmeyen veri yok sayılır. Bu yeni sürümleri bir türün (yani, daha fazla alan içeren bir sürüm) kullanan uygulamalar sağlar, eski sürümleri aynı türde beklediğiniz uygulamalar bilgileri göndermek için.

Aşağıdaki örnekte, `CountryField` `Address` sınıfının sürüm 2,0 ' de yer alan ek veriler, eski bir uygulama daha yeni sürümü seri hale geldiğinde yok sayılır.

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a>Eksik verilerin toleransı

Alanlar, <xref:System.Runtime.Serialization.OptionalFieldAttribute> öznitelikleri uygulanarak isteğe bağlı olarak işaretlenebilir. Seri durumundan çıkarma sırasında isteğe bağlı verileri yoksa, serileştirme motoruna olmaması yoksayar ve bir özel durum oluşturmaz. Bu nedenle, eski sürümleri bir türün beklediğiniz uygulamaları daha yeni sürümleri aynı türde beklediğiniz uygulamaları için veri gönderebilir.

Aşağıdaki örnek, 2.0 sürümünü gösterir `Address` ile `CountryField` alan isteğe bağlı olarak işaretlenmiş. Daha eski bir uygulamanın sürüm 2.0 bekler daha yeni bir uygulama için 1 sürümü gönderirse, veri olmaması göz ardı edilir.

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a>Serileştirme geri çağırmaları

Serileştirme geri çağırmaları serileştirme/seri kaldırma işlemine dört noktalarda hooks sağlayan bir mekanizması mevcuttur.

|Öznitelik|İlişkili yöntem olduğunda çağrılır|Genel kullanım|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Seri durumdan çıkarılamadı.\*|İsteğe bağlı alanları için varsayılan değerler başlatır.|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Seri durumundan çıkarma sonra.|İsteğe bağlı alan değerlerini diğer alanları içeriğe göre düzeltin.|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Serileştirme önce.|Serileştirme için hazırlayın. Örneğin, isteğe bağlı veri yapıları oluşturun.|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Serileştirme sonra.|Serileştirme olayları kaydeder.|

 \*Bu geri çağırma, bir tane varsa, seri durumdan çıkarma oluşturucusundan önce çağrılır.

#### <a name="using-callbacks"></a>Geri çağırmaları kullanma

Geri çağırmaları kullanmak için, uygun özniteliği <xref:System.Runtime.Serialization.StreamingContext> parametreyi kabul eden bir yönteme uygulayın. Her sınıf için yalnızca bir yöntem bu özniteliklerin her biriyle işaretlenebilir. Örneğin:

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

Bu yöntemlerin kullanım için sürüm oluşturma yöneliktir. Veri alanı için eksikse seri durumundan çıkarma sırasında isteğe bağlı bir alan doğru şekilde başlatılmamış olabilir. Bu, doğru değeri atayan ve sonra **OnDeserializingAttribute** veya **OnDeserializedAttribute** özniteliğini uygulayan yöntemi oluşturularak düzeltilebilir.

Aşağıdaki örnekte, yöntem bir tür bağlamında gösterir. Bir uygulamanın daha önceki bir sürümü örneği gönderirse `Address` uygulama daha sonraki bir sürümüyle sınıfına `CountryField` veri alanının eksik olacaktır. Ancak serisini kaldırdıktan sonra, alan varsayılan "Japonya" değerine ayarlanır.

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a>VersionAdded özelliği

**OptionalFieldAttribute** , **VersionAdded** özelliğine sahiptir. .NET Framework sürüm 2,0 ' de, bu kullanılmaz. Ancak, türün gelecekteki serileştirme altyapılarıyla uyumlu olmasını sağlamak için bu özelliğin doğru ayarlanması önemlidir.

Özelliği belirli bir alanı eklenmiş olan bir tür hangi sürümünü gösterir. Tam olarak bir (2 konumunda başlayarak) tarafından arttırılarak türü, aşağıdaki örnekte gösterildiği gibi değiştirilir her zaman:

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a>SerializationBinder

Bazı kullanıcıların, sunucu ve istemci üzerinde farklı bir sınıf sürümü gerektiğinden, seri hale getirilecek ve seri durumdan çıkarılacak sınıfı kontrol etmeniz gerekebilir. <xref:System.Runtime.Serialization.SerializationBinder>serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türleri denetlemek için kullanılan soyut bir sınıftır. Bu sınıf kullanmak için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemleri. Daha fazla bilgi için bkz. [Serializationciltçi Ile serileştirme ve serisini kaldırma](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).

## <a name="best-practices"></a>En iyi uygulamalar

Uygun sürüm davranış sağlamak için bir tür sürümü sürümü değişiklik yapıldığında bu kuralları izleyin:

- Hiçbir zaman serileştirilmiş bir alan kaldırın.
- Özniteliği önceki sürümdeki <xref:System.NonSerializedAttribute> alana uygulanmadıysa, bir alana özniteliği hiçbir şekilde uygulamayın.
- Hiçbir zaman adı veya serileştirilmiş bir alan türünü değiştirin.
- Yeni bir seri hale getirilmiş alan eklerken **OptionalFieldAttribute** özniteliğini uygulayın.
- Bir alandan **Serializedattribute** özniteliği kaldırılırken (önceki bir sürümde seri hale getirilebilir olmayan), **OptionalFieldAttribute** özniteliğini uygulayın.
- Varsayılan değer kabul edilebilir olarak 0 veya **null** olmadığı sürece, tüm isteğe bağlı alanlar için serileştirme geri çağırmaları kullanarak anlamlı varsayılanlar ayarlayın.

Bir tür gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için aşağıdaki yönergeleri izleyin:

- **OptionalFieldAttribute** özniteliğinde her zaman **VersionAdded** özelliğini doğru olarak ayarlayın.
- Dallı sürüm özen gösterin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [İkili serileştirme](binary-serialization.md)
