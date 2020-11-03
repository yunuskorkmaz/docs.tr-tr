---
title: Sürüm dayanıklı serileştirme
description: Seri hale getirilebilir türler üzerinde değişiklik yapmayı kolaylaştıran bir dizi özellik olan sürüm dayanıklı serileştirme hakkında bilgi edinin.
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
ms.openlocfilehash: e7c4d6ca4c72390c3e0803502aa9c1a675e02345
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282417"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="d0107-103">Sürüm dayanıklı serileştirme</span><span class="sxs-lookup"><span data-stu-id="d0107-103">Version tolerant serialization</span></span>

<span data-ttu-id="d0107-104">.NET Framework en eski sürümlerinde, bir uygulamanın bir sürümünden bir sonrakine yeniden kullanılabilir olan serileştirilebilir türler oluşturma işlemi sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="d0107-104">In the earliest versions of .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="d0107-105">Bir tür ek alanlar eklenerek değiştirilmişse, aşağıdaki sorunlar meydana gelir:</span><span class="sxs-lookup"><span data-stu-id="d0107-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="d0107-106">Bir uygulamanın eski sürümleri yeni sürümleri eski türünü seri durumdan çıkarılacak sorulduğunda özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="d0107-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="d0107-107">Bir uygulamanın daha yeni sürümleri, bir eksik veri türüyle eski sürümleri işlenirken özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="d0107-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="d0107-108">Sürüm dayanıklı serileştirme (VTS), seri hale getirilebilir türlerin değiştirilmesini kolaylaştırmak için zaman içinde daha kolay hale getiren bir özellikler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d0107-108">Version Tolerant Serialization (VTS) is a set of features that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="d0107-109">Özellikle, VTS özellikleri, <xref:System.SerializableAttribute> Genel türler dahil olmak üzere özniteliğin uygulandığı sınıflar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="d0107-110">VTS türü diğer sürümleriyle uyumluluk bozup olmadan bu sınıflar için yeni alanlar eklemek olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="d0107-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="d0107-111">Çalışan bir örnek uygulama için bkz. [Sürüm dayanıklı serileştirme teknolojisi örneği](basic-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d0107-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="d0107-112">Kullanırken VTS özelliklerin etkinleştirilip <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="d0107-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="d0107-113">Ayrıca, ' yi kullanırken, fazlalık veri toleransı hariç tüm özellikler de etkinleştirilir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="d0107-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="d0107-114">Serileştirme için bu sınıfları kullanma hakkında daha fazla bilgi için bkz. [Ikili serileştirme](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d0107-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="d0107-115">Özellik listesi</span><span class="sxs-lookup"><span data-stu-id="d0107-115">Feature list</span></span>

<span data-ttu-id="d0107-116">Özellik kümesi, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="d0107-116">The set of features includes the following:</span></span>

- <span data-ttu-id="d0107-117">Gereksiz veya beklenmeyen verilerin toleransı.</span><span class="sxs-lookup"><span data-stu-id="d0107-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="d0107-118">Bu türü için eski sürümleri veri göndermek için yeni bir sürümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0107-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="d0107-119">İsteğe bağlı veriler eksik tolerans.</span><span class="sxs-lookup"><span data-stu-id="d0107-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="d0107-120">Bu yeni sürümleri için veri göndermek eski sürümleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0107-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="d0107-121">Serileştirme geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="d0107-121">Serialization callbacks.</span></span> <span data-ttu-id="d0107-122">Bu veri eksik olduğu durumlarda akıllı varsayılan değer ayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0107-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="d0107-123">Ayrıca, yeni bir isteğe bağlı alan eklendiğinde bildirmek için bir özellik yok.</span><span class="sxs-lookup"><span data-stu-id="d0107-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="d0107-124">Bu, <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliğinin özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d0107-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="d0107-125">Bu özellikler, aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0107-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="d0107-126">Gereksiz veya beklenmeyen verilerin toleransı</span><span class="sxs-lookup"><span data-stu-id="d0107-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="d0107-127">Geçmişte, seri durumundan çıkarma sırasında, hiçbir gereksiz veya beklenmeyen veriler özel durum oluşturulmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="d0107-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="d0107-128">VTS ile aynı durumda, özel durumların oluşturulması yerine hiçbir gereksiz veya beklenmeyen veri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d0107-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="d0107-129">Bu yeni sürümleri bir türün (yani, daha fazla alan içeren bir sürüm) kullanan uygulamalar sağlar, eski sürümleri aynı türde beklediğiniz uygulamalar bilgileri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="d0107-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="d0107-130">Aşağıdaki örnekte, sınıfının sürüm 2,0 ' de yer alan ek veriler, `CountryField` `Address` eski bir uygulama daha yeni sürümü seri hale geldiğinde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d0107-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

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

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="d0107-131">Eksik verilerin toleransı</span><span class="sxs-lookup"><span data-stu-id="d0107-131">Tolerance of missing data</span></span>

<span data-ttu-id="d0107-132">Alanlar, öznitelikleri uygulanarak isteğe bağlı olarak işaretlenebilir <xref:System.Runtime.Serialization.OptionalFieldAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d0107-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="d0107-133">Seri durumundan çıkarma sırasında isteğe bağlı verileri yoksa, serileştirme motoruna olmaması yoksayar ve bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d0107-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="d0107-134">Bu nedenle, eski sürümleri bir türün beklediğiniz uygulamaları daha yeni sürümleri aynı türde beklediğiniz uygulamaları için veri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="d0107-135">Aşağıdaki örnek, 2.0 sürümünü gösterir `Address` ile `CountryField` alan isteğe bağlı olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="d0107-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="d0107-136">Daha eski bir uygulamanın sürüm 2.0 bekler daha yeni bir uygulama için 1 sürümü gönderirse, veri olmaması göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

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
  
### <a name="serialization-callbacks"></a><span data-ttu-id="d0107-137">Serileştirme geri çağırmaları</span><span class="sxs-lookup"><span data-stu-id="d0107-137">Serialization callbacks</span></span>

<span data-ttu-id="d0107-138">Serileştirme geri çağırmaları serileştirme/seri kaldırma işlemine dört noktalarda hooks sağlayan bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d0107-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="d0107-139">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0107-139">Attribute</span></span>|<span data-ttu-id="d0107-140">İlişkili yöntem olduğunda çağrılır</span><span class="sxs-lookup"><span data-stu-id="d0107-140">When the Associated Method is Called</span></span>|<span data-ttu-id="d0107-141">Genel kullanım</span><span class="sxs-lookup"><span data-stu-id="d0107-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="d0107-142">Seri durumdan çıkarılamadı.\*</span><span class="sxs-lookup"><span data-stu-id="d0107-142">Before deserialization.\*</span></span>|<span data-ttu-id="d0107-143">İsteğe bağlı alanları için varsayılan değerler başlatır.</span><span class="sxs-lookup"><span data-stu-id="d0107-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="d0107-144">Seri durumundan çıkarma sonra.</span><span class="sxs-lookup"><span data-stu-id="d0107-144">After deserialization.</span></span>|<span data-ttu-id="d0107-145">İsteğe bağlı alan değerlerini diğer alanları içeriğe göre düzeltin.</span><span class="sxs-lookup"><span data-stu-id="d0107-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="d0107-146">Serileştirme önce.</span><span class="sxs-lookup"><span data-stu-id="d0107-146">Before serialization.</span></span>|<span data-ttu-id="d0107-147">Serileştirme için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-147">Prepare for serialization.</span></span> <span data-ttu-id="d0107-148">Örneğin, isteğe bağlı veri yapıları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0107-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="d0107-149">Serileştirme sonra.</span><span class="sxs-lookup"><span data-stu-id="d0107-149">After serialization.</span></span>|<span data-ttu-id="d0107-150">Serileştirme olayları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0107-150">Log serialization events.</span></span>|

 <span data-ttu-id="d0107-151">\* Bu geri çağırma, bir tane varsa, seri durumdan çıkarma oluşturucusundan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d0107-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="d0107-152">Geri çağırmaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d0107-152">Using callbacks</span></span>

<span data-ttu-id="d0107-153">Geri çağırmaları kullanmak için, uygun özniteliği parametreyi kabul eden bir yönteme uygulayın <xref:System.Runtime.Serialization.StreamingContext> .</span><span class="sxs-lookup"><span data-stu-id="d0107-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="d0107-154">Her sınıf için yalnızca bir yöntem bu özniteliklerin her biriyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="d0107-155">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d0107-155">For example:</span></span>

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

<span data-ttu-id="d0107-156">Bu yöntemlerin kullanım için sürüm oluşturma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d0107-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="d0107-157">Veri alanı için eksikse seri durumundan çıkarma sırasında isteğe bağlı bir alan doğru şekilde başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="d0107-158">Bu, doğru değeri atayan ve sonra **OnDeserializingAttribute** veya **OnDeserializedAttribute** özniteliğini uygulayan yöntemi oluşturularak düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="d0107-159">Aşağıdaki örnekte, yöntem bir tür bağlamında gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0107-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="d0107-160">Bir uygulamanın daha önceki bir sürümü örneği gönderirse `Address` uygulama daha sonraki bir sürümüyle sınıfına `CountryField` veri alanının eksik olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d0107-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="d0107-161">Ancak serisini kaldırdıktan sonra, alan varsayılan "Japonya" değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d0107-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

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

## <a name="the-versionadded-property"></a><span data-ttu-id="d0107-162">VersionAdded özelliği</span><span class="sxs-lookup"><span data-stu-id="d0107-162">The VersionAdded property</span></span>

<span data-ttu-id="d0107-163">**OptionalFieldAttribute** , **VersionAdded** özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d0107-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="d0107-164">Özelliği belirli bir alanı eklenmiş olan bir tür hangi sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0107-164">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="d0107-165">Tam olarak bir (2 konumunda başlayarak) tarafından arttırılarak türü, aşağıdaki örnekte gösterildiği gibi değiştirilir her zaman:</span><span class="sxs-lookup"><span data-stu-id="d0107-165">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

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

## <a name="serializationbinder"></a><span data-ttu-id="d0107-166">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="d0107-166">SerializationBinder</span></span>

<span data-ttu-id="d0107-167">Bazı kullanıcıların, sunucu ve istemci üzerinde farklı bir sınıf sürümü gerektiğinden, seri hale getirilecek ve seri durumdan çıkarılacak sınıfı kontrol etmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d0107-167">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="d0107-168"><xref:System.Runtime.Serialization.SerializationBinder> serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türleri denetlemek için kullanılan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d0107-168"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="d0107-169">Bu sınıf kullanmak için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d0107-169">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="d0107-170">Daha fazla bilgi için bkz. [Serializationciltçi Ile serileştirme ve serisini kaldırma](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="d0107-170">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="d0107-171">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d0107-171">Best practices</span></span>

<span data-ttu-id="d0107-172">Uygun sürüm davranış sağlamak için bir tür sürümü sürümü değişiklik yapıldığında bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d0107-172">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="d0107-173">Hiçbir zaman serileştirilmiş bir alan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d0107-173">Never remove a serialized field.</span></span>
- <span data-ttu-id="d0107-174"><xref:System.NonSerializedAttribute>Özniteliği önceki sürümdeki alana uygulanmadıysa, bir alana özniteliği hiçbir şekilde uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-174">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="d0107-175">Hiçbir zaman adı veya serileştirilmiş bir alan türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0107-175">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="d0107-176">Yeni bir seri hale getirilmiş alan eklerken **OptionalFieldAttribute** özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-176">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="d0107-177">Bir alandan **Serializedattribute** özniteliği kaldırılırken (önceki bir sürümde seri hale getirilebilir olmayan), **OptionalFieldAttribute** özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-177">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="d0107-178">Varsayılan değer kabul edilebilir olarak 0 veya **null** olmadığı sürece, tüm isteğe bağlı alanlar için serileştirme geri çağırmaları kullanarak anlamlı varsayılanlar ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-178">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="d0107-179">Bir tür gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="d0107-179">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="d0107-180">**OptionalFieldAttribute** özniteliğinde her zaman **VersionAdded** özelliğini doğru olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0107-180">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="d0107-181">Dallı sürüm özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="d0107-181">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0107-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0107-182">See also</span></span>

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
- [<span data-ttu-id="d0107-183">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="d0107-183">Binary Serialization</span></span>](binary-serialization.md)
