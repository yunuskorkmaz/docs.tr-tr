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
# <a name="version-tolerant-serialization"></a><span data-ttu-id="b4526-102">Sürüm dayanıklı serileştirme</span><span class="sxs-lookup"><span data-stu-id="b4526-102">Version tolerant serialization</span></span>

<span data-ttu-id="b4526-103">Sonraki uygulamaya bir sürümünden yeniden kullanılabilir olacaktır serializable türler oluşturmak sürüm 1.0 ve 1.1 .NET Framework'ün, sorunlu.</span><span class="sxs-lookup"><span data-stu-id="b4526-103">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="b4526-104">Bir tür ek alanlar eklenerek değiştirilmişse, aşağıdaki sorunlar meydana gelir:</span><span class="sxs-lookup"><span data-stu-id="b4526-104">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="b4526-105">Bir uygulamanın eski sürümleri yeni sürümleri eski türünü seri durumdan çıkarılacak sorulduğunda özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="b4526-105">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="b4526-106">Bir uygulamanın daha yeni sürümleri, bir eksik veri türüyle eski sürümleri işlenirken özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="b4526-106">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="b4526-107">Sürüm dayanıklı serileştirme (VTS), .NET Framework 2,0 ' de sunulan ve zaman içinde seri hale getirilebilir türlerin değiştirilmesini sağlayan bir özellik kümesidir.</span><span class="sxs-lookup"><span data-stu-id="b4526-107">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="b4526-108">Özellikle, VTS özellikleri, genel türler de dahil olmak üzere <xref:System.SerializableAttribute> özniteliğinin uygulandığı sınıflar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-108">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="b4526-109">VTS türü diğer sürümleriyle uyumluluk bozup olmadan bu sınıflar için yeni alanlar eklemek olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="b4526-109">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="b4526-110">Çalışan bir örnek uygulama için bkz. [Sürüm dayanıklı serileştirme teknolojisi örneği](version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4526-110">For a working sample application, see [Version Tolerant Serialization Technology Sample](version-tolerant-serialization-technology-sample.md).</span></span>

<span data-ttu-id="b4526-111">Kullanırken VTS özelliklerin etkinleştirilip <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="b4526-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="b4526-112">Ayrıca, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>kullanılırken, fazlalık veri toleransı hariç tüm özellikler de etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="b4526-113">Serileştirme için bu sınıfları kullanma hakkında daha fazla bilgi için bkz. [Ikili serileştirme](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b4526-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="b4526-114">Özellik listesi</span><span class="sxs-lookup"><span data-stu-id="b4526-114">Feature list</span></span>

<span data-ttu-id="b4526-115">Özellik kümesi, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b4526-115">The set of features includes the following:</span></span>

- <span data-ttu-id="b4526-116">Gereksiz veya beklenmeyen verilerin toleransı.</span><span class="sxs-lookup"><span data-stu-id="b4526-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="b4526-117">Bu türü için eski sürümleri veri göndermek için yeni bir sürümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4526-117">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="b4526-118">İsteğe bağlı veriler eksik tolerans.</span><span class="sxs-lookup"><span data-stu-id="b4526-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="b4526-119">Bu yeni sürümleri için veri göndermek eski sürümleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4526-119">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="b4526-120">Serileştirme geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="b4526-120">Serialization callbacks.</span></span> <span data-ttu-id="b4526-121">Bu veri eksik olduğu durumlarda akıllı varsayılan değer ayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4526-121">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="b4526-122">Ayrıca, yeni bir isteğe bağlı alan eklendiğinde bildirmek için bir özellik yok.</span><span class="sxs-lookup"><span data-stu-id="b4526-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="b4526-123">Bu, <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliğinin <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b4526-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="b4526-124">Bu özellikler, aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="b4526-124">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="b4526-125">Gereksiz veya beklenmeyen verilerin toleransı</span><span class="sxs-lookup"><span data-stu-id="b4526-125">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="b4526-126">Geçmişte, seri durumundan çıkarma sırasında, hiçbir gereksiz veya beklenmeyen veriler özel durum oluşturulmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="b4526-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="b4526-127">VTS ile aynı durumda, özel durumların oluşturulması yerine hiçbir gereksiz veya beklenmeyen veri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b4526-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="b4526-128">Bu yeni sürümleri bir türün (yani, daha fazla alan içeren bir sürüm) kullanan uygulamalar sağlar, eski sürümleri aynı türde beklediğiniz uygulamalar bilgileri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="b4526-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="b4526-129">Aşağıdaki örnekte, `Address` sınıfının 2,0 sürümünün `CountryField` bulunan ek veriler, eski bir uygulama daha yeni sürümü seri hale geldiğinde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b4526-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

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

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="b4526-130">Eksik verilerin toleransı</span><span class="sxs-lookup"><span data-stu-id="b4526-130">Tolerance of missing data</span></span>

<span data-ttu-id="b4526-131">Alanlar, <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliği bunlara uygulanarak isteğe bağlı olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="b4526-132">Seri durumundan çıkarma sırasında isteğe bağlı verileri yoksa, serileştirme motoruna olmaması yoksayar ve bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="b4526-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="b4526-133">Bu nedenle, eski sürümleri bir türün beklediğiniz uygulamaları daha yeni sürümleri aynı türde beklediğiniz uygulamaları için veri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="b4526-134">Aşağıdaki örnek, 2.0 sürümünü gösterir `Address` ile `CountryField` alan isteğe bağlı olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="b4526-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="b4526-135">Daha eski bir uygulamanın sürüm 2.0 bekler daha yeni bir uygulama için 1 sürümü gönderirse, veri olmaması göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

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
  
### <a name="serialization-callbacks"></a><span data-ttu-id="b4526-136">Serileştirme geri çağırmaları</span><span class="sxs-lookup"><span data-stu-id="b4526-136">Serialization callbacks</span></span>

<span data-ttu-id="b4526-137">Serileştirme geri çağırmaları serileştirme/seri kaldırma işlemine dört noktalarda hooks sağlayan bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b4526-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="b4526-138">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b4526-138">Attribute</span></span>|<span data-ttu-id="b4526-139">İlişkili yöntem olduğunda çağrılır</span><span class="sxs-lookup"><span data-stu-id="b4526-139">When the Associated Method is Called</span></span>|<span data-ttu-id="b4526-140">Genel kullanım</span><span class="sxs-lookup"><span data-stu-id="b4526-140">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="b4526-141">Seri durumdan çıkarılamadı.\*</span><span class="sxs-lookup"><span data-stu-id="b4526-141">Before deserialization.\*</span></span>|<span data-ttu-id="b4526-142">İsteğe bağlı alanları için varsayılan değerler başlatır.</span><span class="sxs-lookup"><span data-stu-id="b4526-142">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="b4526-143">Seri durumundan çıkarma sonra.</span><span class="sxs-lookup"><span data-stu-id="b4526-143">After deserialization.</span></span>|<span data-ttu-id="b4526-144">İsteğe bağlı alan değerlerini diğer alanları içeriğe göre düzeltin.</span><span class="sxs-lookup"><span data-stu-id="b4526-144">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="b4526-145">Serileştirme önce.</span><span class="sxs-lookup"><span data-stu-id="b4526-145">Before serialization.</span></span>|<span data-ttu-id="b4526-146">Serileştirme için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-146">Prepare for serialization.</span></span> <span data-ttu-id="b4526-147">Örneğin, isteğe bağlı veri yapıları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4526-147">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="b4526-148">Serileştirme sonra.</span><span class="sxs-lookup"><span data-stu-id="b4526-148">After serialization.</span></span>|<span data-ttu-id="b4526-149">Serileştirme olayları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b4526-149">Log serialization events.</span></span>|

 <span data-ttu-id="b4526-150">Bu geri çağırma, varsa seri kaldırma oluşturucusundan önce çağrılır. \*</span><span class="sxs-lookup"><span data-stu-id="b4526-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="b4526-151">Geri çağırmaları kullanma</span><span class="sxs-lookup"><span data-stu-id="b4526-151">Using callbacks</span></span>

<span data-ttu-id="b4526-152">Geri çağırmaları kullanmak için, <xref:System.Runtime.Serialization.StreamingContext> parametresi kabul eden bir yönteme uygun özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="b4526-153">Her sınıf için yalnızca bir yöntem bu özniteliklerin her biriyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="b4526-154">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b4526-154">For example:</span></span>

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

<span data-ttu-id="b4526-155">Bu yöntemlerin kullanım için sürüm oluşturma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b4526-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="b4526-156">Veri alanı için eksikse seri durumundan çıkarma sırasında isteğe bağlı bir alan doğru şekilde başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="b4526-157">Bu, doğru değeri atayan ve sonra **OnDeserializingAttribute** veya **OnDeserializedAttribute** özniteliğini uygulayan yöntemi oluşturularak düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="b4526-158">Aşağıdaki örnekte, yöntem bir tür bağlamında gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4526-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="b4526-159">Bir uygulamanın daha önceki bir sürümü örneği gönderirse `Address` uygulama daha sonraki bir sürümüyle sınıfına `CountryField` veri alanının eksik olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b4526-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="b4526-160">Ancak serisini kaldırdıktan sonra, alan varsayılan "Japonya" değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b4526-160">But after deserialization, the field will be set to a default value "Japan".</span></span>

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

## <a name="the-versionadded-property"></a><span data-ttu-id="b4526-161">VersionAdded özelliği</span><span class="sxs-lookup"><span data-stu-id="b4526-161">The VersionAdded property</span></span>

<span data-ttu-id="b4526-162">**OptionalFieldAttribute** , **VersionAdded** özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4526-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="b4526-163">.NET Framework sürüm 2,0 ' de, bu kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b4526-163">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="b4526-164">Ancak, türün gelecekteki serileştirme altyapılarıyla uyumlu olmasını sağlamak için bu özelliğin doğru ayarlanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b4526-164">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="b4526-165">Özelliği belirli bir alanı eklenmiş olan bir tür hangi sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4526-165">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="b4526-166">Tam olarak bir (2 konumunda başlayarak) tarafından arttırılarak türü, aşağıdaki örnekte gösterildiği gibi değiştirilir her zaman:</span><span class="sxs-lookup"><span data-stu-id="b4526-166">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

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

## <a name="serializationbinder"></a><span data-ttu-id="b4526-167">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="b4526-167">SerializationBinder</span></span>

<span data-ttu-id="b4526-168">Bazı kullanıcıların, sunucu ve istemci üzerinde farklı bir sınıf sürümü gerektiğinden, seri hale getirilecek ve seri durumdan çıkarılacak sınıfı kontrol etmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b4526-168">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="b4526-169"><xref:System.Runtime.Serialization.SerializationBinder> serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türleri denetlemek için kullanılan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b4526-169"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="b4526-170">Bu sınıf kullanmak için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b4526-170">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="b4526-171">Daha fazla bilgi için bkz. [Serializationciltçi Ile serileştirme ve serisini kaldırma](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="b4526-171">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="b4526-172">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b4526-172">Best practices</span></span>

<span data-ttu-id="b4526-173">Uygun sürüm davranış sağlamak için bir tür sürümü sürümü değişiklik yapıldığında bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b4526-173">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="b4526-174">Hiçbir zaman serileştirilmiş bir alan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b4526-174">Never remove a serialized field.</span></span>
- <span data-ttu-id="b4526-175">Özniteliği önceki sürümdeki alana uygulanmadıysa, bir alana <xref:System.NonSerializedAttribute> özniteliğini hiçbir şekilde uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-175">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="b4526-176">Hiçbir zaman adı veya serileştirilmiş bir alan türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b4526-176">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="b4526-177">Yeni bir seri hale getirilmiş alan eklerken **OptionalFieldAttribute** özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-177">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="b4526-178">Bir alandan **Serializedattribute** özniteliği kaldırılırken (önceki bir sürümde seri hale getirilebilir olmayan), **OptionalFieldAttribute** özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-178">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="b4526-179">Varsayılan değer kabul edilebilir olarak 0 veya **null** olmadığı sürece, tüm isteğe bağlı alanlar için serileştirme geri çağırmaları kullanarak anlamlı varsayılanlar ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-179">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="b4526-180">Bir tür gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="b4526-180">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="b4526-181">**OptionalFieldAttribute** özniteliğinde her zaman **VersionAdded** özelliğini doğru olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b4526-181">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="b4526-182">Dallı sürüm özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="b4526-182">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4526-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4526-183">See also</span></span>

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
- [<span data-ttu-id="b4526-184">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b4526-184">Binary Serialization</span></span>](binary-serialization.md)
