---
title: Sürüme dayanıklı serileştirme
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
ms.openlocfilehash: a61fa5a3f87c534574d7265dfdc16365c0afbbe0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644861"
---
# <a name="version-tolerant-serialization"></a>Sürüme dayanıklı serileştirme
Sonraki uygulamaya bir sürümünden yeniden kullanılabilir olacaktır serializable türler oluşturmak sürüm 1.0 ve 1.1 .NET Framework'ün, sorunlu. Bir tür ek alanlar ekleyerek değiştirilmişse, aşağıdaki sorunları ortaya çıkabilecek:  
  
- Bir uygulamanın eski sürümleri yeni sürümleri eski türünü seri durumdan çıkarılacak sorulduğunda özel durumlar oluşturan.  
  
- Bir uygulamanın daha yeni sürümleri, bir eksik veri türüyle eski sürümleri işlenirken özel durumlar oluşturan.  
  
 Sürüm dengeleyici seri hale getirme (VTS), serializable türler değiştirmek için zamanla kolaylaştırır .NET Framework 2.0 sunulan özellikleri kümesidir. Özellikle hangi sınıflar için VTS özellikleri etkin <xref:System.SerializableAttribute> özniteliği uygulandı, genel türler dahil olmak üzere. VTS türü diğer sürümleriyle uyumluluk bozup olmadan bu sınıflar için yeni alanlar eklemek olanaklı kılar. Çalışan bir örnek uygulama için bkz. [sürüme dayanıklı serileştirme teknolojisi örneği](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).  
  
 Kullanırken VTS özelliklerin etkinleştirilip <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Ayrıca, yabancı veri tolerans hariç tüm özellikleri de kullanırken etkinleştirilir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Serileştirme için bu sınıflar kullanma hakkında daha fazla bilgi için bkz. [ikili serileştirme](binary-serialization.md).  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Özellik listesi  
 Özellik kümesi, aşağıdakileri içerir:  
  
- Yabancı veya beklenmeyen veri tolerans. Bu türü için eski sürümleri veri göndermek için yeni bir sürümü sağlar.  
  
- İsteğe bağlı veriler eksik tolerans. Bu yeni sürümleri için veri göndermek eski sürümleri sağlar.  
  
- Serileştirme geri çağırmaları. Bu veri eksik olduğu durumlarda akıllı varsayılan değer ayarı sağlar.  
  
 Ayrıca, yeni bir isteğe bağlı alan eklendiğinde bildirmek için bir özellik yok. Bu <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> özelliği <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliği.  
  
 Bu özellikleri aşağıda daha ayrıntılı olarak açıklanır.  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a>Yabancı veya beklenmeyen veri tolerans  
 Herhangi bir yabancı veya beklenmeyen veri seri durumundan çıkarma sırasında geçmiş, özel durum oluşturulmasına neden oldu. VTS ile aynı durumda herhangi bir yabancı veya beklenmeyen veri özel durum oluşturulmasına neden yerine göz ardı edilir. Bu yeni sürümleri bir türün (yani, daha fazla alan içeren bir sürüm) kullanan uygulamalar sağlar, eski sürümleri aynı türde beklediğiniz uygulamalar bilgileri göndermek için.  
  
 Aşağıdaki örnekte, ek veriler içindeki `CountryField` 2.0 sürümünü `Address` sınıf göz ardı edilir olduğunda daha eski bir uygulamanın yeni sürümü seri durumdan çıkarır.  
  
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
  
## <a name="tolerance-of-missing-data"></a>Eksik veri tolerans  
 Alanları işaretlenir isteğe bağlı olarak uygulayarak <xref:System.Runtime.Serialization.OptionalFieldAttribute> öznitelik. Seri durumundan çıkarma sırasında isteğe bağlı verileri yoksa, serileştirme motoruna olmaması yoksayar ve bir özel durum oluşturmaz. Bu nedenle, eski sürümleri bir türün beklediğiniz uygulamaları daha yeni sürümleri aynı türde beklediğiniz uygulamaları için veri gönderebilir.  
  
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
  
## <a name="serialization-callbacks"></a>Serileştirme geri çağırmaları  
 Serileştirme geri çağırmaları serileştirme/seri kaldırma işlemine dört noktalarda hooks sağlayan bir mekanizması mevcuttur.  
  
|Öznitelik|İlişkili yöntem olduğunda çağrılır|Genel kullanım|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Önce deserialization.*|İsteğe bağlı alanları için varsayılan değerler başlatır.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Seri durumundan çıkarma sonra.|İsteğe bağlı alan değerlerini diğer alanları içeriğe göre düzeltin.|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Serileştirme önce.|Serileştirme için hazırlayın. Örneğin, isteğe bağlı veri yapılarını oluşturun.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Serileştirme sonra.|Serileştirme olayları kaydeder.|  
  
 \* Varsa, bu geri çağırma seri durumdan çıkarma Oluşturucusu önce çağrılır.  
  
### <a name="using-callbacks"></a>Geri çağırmaları kullanarak  
 Geri çağırmaları kullanmak için kabul eden bir yönteme uygun öznitelik geçerli bir <xref:System.Runtime.Serialization.StreamingContext> parametresi. Sınıf başına yalnızca bir yöntem her bu öznitelikler işaretlenebilir. Örneğin:  
  
```csharp  
[OnDeserializing]  
private void SetCountryRegionDefault(StreamingContext sc)  
{  
    CountryField = "Japan";  
}  
```  
  
```vb  
<OnDeserializing>  
Private Sub SetCountryRegionDefault(StreamingContext sc)  
    CountryField = "Japan";  
End Sub  
```  
  
 Bu yöntemlerin kullanım için sürüm oluşturma yöneliktir. Veri alanı için eksikse seri durumundan çıkarma sırasında isteğe bağlı bir alan doğru şekilde başlatılmamış olabilir. Bu doğru değeri atar yöntemi oluşturma, sonra ya da uygulama düzeltilebilir **OnDeserializingAttribute** veya **OnDeserializedAttribute** özniteliğini yöntemine.  
  
 Aşağıdaki örnekte, yöntem bir tür bağlamında gösterir. Bir uygulamanın daha önceki bir sürümü örneği gönderirse `Address` uygulama daha sonraki bir sürümüyle sınıfına `CountryField` veri alanının eksik olacaktır. Ancak seri durumundan çıkarma sonra alanı bir varsayılan değer "Japonya." ayarlanacaktır.  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    [OptionalField]  
    public string CountryField;  
  
    [OnDeserializing]  
    private void SetCountryRegionDefault (StreamingContext sc)  
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
    Private Sub SetCountryRegionDefault(StreamingContext sc)  
        CountryField = "Japan";  
    End Sub  
End Class  
```  
  
## <a name="the-versionadded-property"></a>VersionAdded özelliği  
 **OptionalFieldAttribute** sahip **VersionAdded** özelliği. .NET Framework'ün 2.0 sürümünde, bu kullanılmaz. Ancak, bu özellik türü gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için doğru şekilde ayarlanması önemlidir.  
  
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
 Bazı kullanıcılar, hangi sınıfı hale getirmek ve farklı bir sürüm sınıfının sunucu ve istemci olması gerektiğinden serisini kaldırmak için Denetim gerekebilir. <xref:System.Runtime.Serialization.SerializationBinder> bir Özet sınıf serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır.  Bu sınıf kullanmak için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemleri. Daha fazla bilgi için [denetleme serileştirme ve seri durumundan çıkarma SerializationBinder ile](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).  
  
## <a name="best-practices"></a>Önerilen uygulamalar  
 Uygun sürüm davranış sağlamak için bir tür sürümü sürümü değişiklik yapıldığında bu kuralları izleyin:  
  
- Hiçbir zaman serileştirilmiş bir alan kaldırın.  
  
- Hiçbir zaman uygulamak <xref:System.NonSerializedAttribute> öznitelik önceki sürümü alanına uygulanmamış olması durumunda bir alan öznitelik.  
  
- Hiçbir zaman adı veya serileştirilmiş bir alan türünü değiştirin.  
  
- Yeni bir seri hale getirilmiş alan eklerken uygulamak **OptionalFieldAttribute** özniteliği.  
  
- Kaldırırken bir **NonSerializedAttribute** alanından (önceki bir sürümde serileştirilebilir değildi) bir öznitelik, Uygula **OptionalFieldAttribute** özniteliği.  
  
- Tüm isteğe bağlı alanları için serileştirme geri çağırmaları sürece kullanarak anlamlı varsayılanları ayarlamak 0 veya **null** Varsayılanları kabul edilir.  
  
 Bir tür gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için aşağıdaki yönergeleri izleyin:  
  
- Her zaman **VersionAdded** özelliği **OptionalFieldAttribute** doğru öznitelik.  
  
- Dallı sürüm özen gösterin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [İkili Serileştirme](binary-serialization.md)
