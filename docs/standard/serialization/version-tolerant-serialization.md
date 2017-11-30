---
title: "Sürüm dayanıklı seri hale getirme"
ms.date: 08/08/2017
ms.prod: .net
ms.topic: article
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
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 90f2b1e73a24b0f732eaba4422faa9a1dcc15135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="03cdd-102">Sürüm dayanıklı seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="03cdd-102">Version tolerant serialization</span></span>
<span data-ttu-id="03cdd-103">Sonraki uygulamaya bir sürümünden yeniden kullanılabilir olacaktır serializable türler oluşturmak sürüm 1.0 ve 1.1 .NET Framework'ün, sorunlu.</span><span class="sxs-lookup"><span data-stu-id="03cdd-103">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="03cdd-104">Bir tür ek alanlar ekleyerek değiştirilmişse, aşağıdaki sorunları ortaya çıkabilecek:</span><span class="sxs-lookup"><span data-stu-id="03cdd-104">If a type was modified by adding extra fields, the following problems would occur:</span></span>  
  
-   <span data-ttu-id="03cdd-105">Bir uygulamanın eski sürümleri yeni sürümleri eski türünü seri durumdan çıkarılacak sorulduğunda özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="03cdd-105">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>  
  
-   <span data-ttu-id="03cdd-106">Bir uygulamanın daha yeni sürümleri, bir eksik veri türüyle eski sürümleri işlenirken özel durumlar oluşturan.</span><span class="sxs-lookup"><span data-stu-id="03cdd-106">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>  
  
 <span data-ttu-id="03cdd-107">Sürüm dayanıklı seri hale getirme (VTS), seri hale getirilebilir türler değiştirmek için zamanla kolaylaştırır .NET Framework 2.0 sürümünde sunulan özellikler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-107">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="03cdd-108">Özellikle, VTS özelliklerinin hangi sınıflar için etkin olduğu <xref:System.SerializableAttribute> özniteliği uygulandı, genel türleri dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="03cdd-108">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="03cdd-109">VTS türü diğer sürümleriyle uyumluluk bozup olmadan bu sınıflar için yeni alanlar eklemek olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="03cdd-109">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="03cdd-110">Çalışan bir örnek uygulama için bkz: [sürümü dayanıklı serileştirme teknolojisi örneği](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="03cdd-110">For a working sample application, see [Version Tolerant Serialization Technology Sample](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span></span>  
  
 <span data-ttu-id="03cdd-111">Kullanırken VTS özelliklerin etkinleştirilip <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="03cdd-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="03cdd-112">Ayrıca, gereksiz veri dayanıklılık dışındaki tüm özellikleri de kullanırken etkinleştirilir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="03cdd-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="03cdd-113">Seri hale getirme için bu sınıfları kullanma hakkında daha fazla bilgi için bkz: [ikili seri hale getirme](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="03cdd-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="03cdd-114">Özellik listesi</span><span class="sxs-lookup"><span data-stu-id="03cdd-114">Feature list</span></span>  
 <span data-ttu-id="03cdd-115">Özellik kümesi, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="03cdd-115">The set of features includes the following:</span></span>  
  
-   <span data-ttu-id="03cdd-116">Gereksiz veya beklenmeyen veri tolerans.</span><span class="sxs-lookup"><span data-stu-id="03cdd-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="03cdd-117">Bu türü için eski sürümleri veri göndermek için yeni bir sürümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="03cdd-117">This enables newer versions of the type to send data to older versions.</span></span>  
  
-   <span data-ttu-id="03cdd-118">İsteğe bağlı veriler eksik tolerans.</span><span class="sxs-lookup"><span data-stu-id="03cdd-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="03cdd-119">Bu yeni sürümleri için veri göndermek eski sürümleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="03cdd-119">This enables older versions to send data to newer versions.</span></span>  
  
-   <span data-ttu-id="03cdd-120">Serileştirme geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="03cdd-120">Serialization callbacks.</span></span> <span data-ttu-id="03cdd-121">Bu veri eksik olduğu durumlarda akıllı varsayılan değer ayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="03cdd-121">This enables intelligent default value setting in cases where data is missing.</span></span>  
  
 <span data-ttu-id="03cdd-122">Ayrıca, yeni bir isteğe bağlı alan eklendiğinde bildirmek için bir özellik yok.</span><span class="sxs-lookup"><span data-stu-id="03cdd-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="03cdd-123">Bu <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> özelliğinin <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>  
  
 <span data-ttu-id="03cdd-124">Bu özellikleri aşağıda daha ayrıntılı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-124">These features are discussed in greater detail below.</span></span>  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="03cdd-125">Dayanıklılık yabancı veya beklenmeyen veri</span><span class="sxs-lookup"><span data-stu-id="03cdd-125">Tolerance of extraneous or unexpected data</span></span>  
 <span data-ttu-id="03cdd-126">Geçmişte, seri durumdan çıkarma sırasında durum için özel durumlar herhangi bir yabancı veya beklenmeyen veri neden oldu.</span><span class="sxs-lookup"><span data-stu-id="03cdd-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="03cdd-127">VTS ile aynı durumda, herhangi bir yabancı veya beklenmeyen veri özel durum oluşturulmasına neden yerine göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="03cdd-128">Bu yeni sürümleri bir türün (yani, daha fazla alan içeren bir sürüm) kullanan uygulamalar sağlar, eski sürümleri aynı türde beklediğiniz uygulamalar bilgileri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="03cdd-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>  
  
 <span data-ttu-id="03cdd-129">Aşağıdaki örnekte yer alan ek veriler `CountryField` 2.0 sürümünü `Address` sınıfı, eski uygulamanın yeni sürümü çıkarır, yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>  
  
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
  
## <a name="tolerance-of-missing-data"></a><span data-ttu-id="03cdd-130">Dayanıklılık eksik veri</span><span class="sxs-lookup"><span data-stu-id="03cdd-130">Tolerance of missing data</span></span>  
 <span data-ttu-id="03cdd-131">Alanları işaretlenir isteğe bağlı olarak uygulayarak <xref:System.Runtime.Serialization.OptionalFieldAttribute> onlara özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="03cdd-132">Seri durumundan çıkarma sırasında isteğe bağlı verileri yoksa, serileştirme motoruna olmaması yoksayar ve bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="03cdd-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="03cdd-133">Bu nedenle, eski sürümleri bir türün beklediğiniz uygulamaları daha yeni sürümleri aynı türde beklediğiniz uygulamaları için veri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>  
  
 <span data-ttu-id="03cdd-134">Aşağıdaki örnek, 2.0 sürümünü gösterir `Address` ile `CountryField` alan isteğe bağlı olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="03cdd-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="03cdd-135">Daha eski bir uygulamanın sürüm 2.0 bekler daha yeni bir uygulama için 1 sürümü gönderirse, veri olmaması göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>  
  
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
  
## <a name="serialization-callbacks"></a><span data-ttu-id="03cdd-136">Seri hale getirme geri çağrıları</span><span class="sxs-lookup"><span data-stu-id="03cdd-136">Serialization callbacks</span></span>  
 <span data-ttu-id="03cdd-137">Serileştirme geri çağırmaları serileştirme/seri kaldırma işlemine dört noktalarda hooks sağlayan bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="03cdd-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>  
  
|<span data-ttu-id="03cdd-138">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="03cdd-138">Attribute</span></span>|<span data-ttu-id="03cdd-139">İlişkili yöntem olduğunda çağrılır</span><span class="sxs-lookup"><span data-stu-id="03cdd-139">When the Associated Method is Called</span></span>|<span data-ttu-id="03cdd-140">Genel kullanım</span><span class="sxs-lookup"><span data-stu-id="03cdd-140">Typical Use</span></span>|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="03cdd-141">Önce deserialization.*</span><span class="sxs-lookup"><span data-stu-id="03cdd-141">Before deserialization.*</span></span>|<span data-ttu-id="03cdd-142">İsteğe bağlı alanları için varsayılan değerler başlatır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-142">Initialize default values for optional fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="03cdd-143">Seri durumundan çıkarma sonra.</span><span class="sxs-lookup"><span data-stu-id="03cdd-143">After deserialization.</span></span>|<span data-ttu-id="03cdd-144">İsteğe bağlı alan değerlerini diğer alanları içeriğe göre düzeltin.</span><span class="sxs-lookup"><span data-stu-id="03cdd-144">Fix optional field values based on contents of other fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="03cdd-145">Serileştirme önce.</span><span class="sxs-lookup"><span data-stu-id="03cdd-145">Before serialization.</span></span>|<span data-ttu-id="03cdd-146">Serileştirme için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="03cdd-146">Prepare for serialization.</span></span> <span data-ttu-id="03cdd-147">Örneğin, isteğe bağlı veri yapılarını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="03cdd-147">For example, create optional data structures.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="03cdd-148">Serileştirme sonra.</span><span class="sxs-lookup"><span data-stu-id="03cdd-148">After serialization.</span></span>|<span data-ttu-id="03cdd-149">Serileştirme olayları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="03cdd-149">Log serialization events.</span></span>|  
  
 <span data-ttu-id="03cdd-150">\*Varsa, bu geri çağırma seri durumdan çıkarma Oluşturucusu önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>  
  
### <a name="using-callbacks"></a><span data-ttu-id="03cdd-151">Geri aramalar kullanma</span><span class="sxs-lookup"><span data-stu-id="03cdd-151">Using callbacks</span></span>  
 <span data-ttu-id="03cdd-152">Geri aramalar kullanmak için uygun öznitelik kabul eden bir yönteme uygulamak bir <xref:System.Runtime.Serialization.StreamingContext> parametresi.</span><span class="sxs-lookup"><span data-stu-id="03cdd-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="03cdd-153">Sınıf başına yalnızca bir yöntem bu özniteliklerinin her biriyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="03cdd-154">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="03cdd-154">For example:</span></span>  
  
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
  
 <span data-ttu-id="03cdd-155">Bu yöntemlerin kullanım için sürüm oluşturma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="03cdd-156">Veri alanı için eksikse seri durumundan çıkarma sırasında isteğe bağlı bir alan doğru şekilde başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="03cdd-157">Bu doğru değeri atar yöntemi oluşturma, sonra da uygulama düzeltilebilir **OnDeserializingAttribute** veya **OnDeserializedAttribute** özniteliği yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03cdd-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>  
  
 <span data-ttu-id="03cdd-158">Aşağıdaki örnekte, yöntem bir tür bağlamında gösterir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="03cdd-159">Bir uygulamanın daha önceki bir sürümü örneği gönderirse `Address` uygulama daha sonraki bir sürümüyle sınıfına `CountryField` veri alanının eksik olacaktır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="03cdd-160">Ancak seri durumundan çıkarma sonra alanı bir varsayılan değer "Japonya." ayarlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-160">But after deserialization, the field will be set to a default value "Japan."</span></span>  
  
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
  
## <a name="the-versionadded-property"></a><span data-ttu-id="03cdd-161">VersionAdded özelliği</span><span class="sxs-lookup"><span data-stu-id="03cdd-161">The VersionAdded property</span></span>  
 <span data-ttu-id="03cdd-162">**OptionalFieldAttribute** sahip **VersionAdded** özelliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="03cdd-163">Sürümünde .NET Framework 2.0, bu kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="03cdd-163">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="03cdd-164">Bununla birlikte, bu özellik türü gelecekteki seri hale getirme altyapısı ile uyumlu olduğundan emin olmak için doğru bir şekilde ayarlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-164">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>  
  
 <span data-ttu-id="03cdd-165">Özelliği belirli bir alanı eklenmiş olan bir tür hangi sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-165">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="03cdd-166">Tam olarak bir (2 konumunda başlayarak) tarafından arttırılarak türü, aşağıdaki örnekte gösterildiği gibi değiştirilir her zaman:</span><span class="sxs-lookup"><span data-stu-id="03cdd-166">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>  
  
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
  
## <a name="serializationbinder"></a><span data-ttu-id="03cdd-167">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="03cdd-167">SerializationBinder</span></span>  
 <span data-ttu-id="03cdd-168">Bazı kullanıcılar, hangi sınıfının seri hale getirmek ve seri durumdan sınıfının farklı bir sürümünü sunucu ve istemci gerektirdiğinden denetlemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="03cdd-168">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="03cdd-169"><xref:System.Runtime.Serialization.SerializationBinder>bir Özet sınıf, seri hale getirme ve seri durumdan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03cdd-169"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span>  <span data-ttu-id="03cdd-170">Bu sınıf kullanmak için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="03cdd-170">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="03cdd-171">[Seri hale getirme ve seri durumdan çıkarma SerializationBinder ile denetleme](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="03cdd-171"> [Controlling Serialization and Deserialization with SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="03cdd-172">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="03cdd-172">Best practices</span></span>  
 <span data-ttu-id="03cdd-173">Uygun sürüm davranış sağlamak için bir tür sürümü sürümü değişiklik yapıldığında bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="03cdd-173">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>  
  
-   <span data-ttu-id="03cdd-174">Hiçbir zaman serileştirilmiş bir alan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="03cdd-174">Never remove a serialized field.</span></span>  
  
-   <span data-ttu-id="03cdd-175">Asla uygulama <xref:System.NonSerializedAttribute> öznitelik önceki sürümü alanına uygulanmamışsa bir alan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-175">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>  
  
-   <span data-ttu-id="03cdd-176">Hiçbir zaman adı veya serileştirilmiş bir alan türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="03cdd-176">Never change the name or the type of a serialized field.</span></span>  
  
-   <span data-ttu-id="03cdd-177">Yeni bir seri hale getirilmiş alan eklerken, uygulama **OptionalFieldAttribute** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-177">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>  
  
-   <span data-ttu-id="03cdd-178">Kaldırırken bir **NonSerializedAttribute** özniteliği (, önceki bir sürümde serileştirilebilir olmayan) bir alandan, Uygula **OptionalFieldAttribute** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-178">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>  
  
-   <span data-ttu-id="03cdd-179">Tüm isteğe bağlı alanlar için seri hale getirme geri çağrıları sürece kullanarak anlamlı Varsayılanlarını Ayarla 0 veya **null** Varsayılanları kabul edilebilir olduğundan.</span><span class="sxs-lookup"><span data-stu-id="03cdd-179">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>  
  
 <span data-ttu-id="03cdd-180">Bir tür gelecekteki serileştirme yapısıyla uyumlu olmasını sağlamak için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="03cdd-180">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="03cdd-181">Her zaman **VersionAdded** özelliği **OptionalFieldAttribute** doğru özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03cdd-181">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>  
  
-   <span data-ttu-id="03cdd-182">Dallı sürüm özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="03cdd-182">Avoid branched versioning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03cdd-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03cdd-183">See also</span></span>  
 <xref:System.SerializableAttribute>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 <xref:System.NonSerializedAttribute>  
 [<span data-ttu-id="03cdd-184">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="03cdd-184">Binary Serialization</span></span>](binary-serialization.md)
