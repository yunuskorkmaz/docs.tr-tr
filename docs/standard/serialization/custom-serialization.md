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
ms.openlocfilehash: 60fdc0317975d94433401e3214953b77d0970f60
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741066"
---
# <a name="custom-serialization"></a><span data-ttu-id="36c19-102">Özel serileştirme</span><span class="sxs-lookup"><span data-stu-id="36c19-102">Custom serialization</span></span>
<span data-ttu-id="36c19-103">Özel serileştirme, bir türün serileştirme ve serisini kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="36c19-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="36c19-104">Serileştirme ' i denetleyerek, bir türün sürümleri arasında serileştirme ve seri durumdan çıkarma özelliği olan serileştirme uyumluluğunu sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="36c19-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="36c19-105">Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan.</span><span class="sxs-lookup"><span data-stu-id="36c19-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="36c19-106">Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir.</span><span class="sxs-lookup"><span data-stu-id="36c19-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="36c19-107">Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36c19-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="36c19-108">Aşağıdaki bölümlerde serileştirme denetiminin nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="36c19-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="36c19-109">.NET Framework 4,0 ' den önceki sürümlerde, kısmen güvenilen bir derlemede özel kullanıcı verilerinin serileştirilmesi, GetObjectData kullanılarak gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="36c19-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="36c19-110">Sürüm 4,0 ' den başlayarak, bu yöntem kısmen güvenilen derlemelerde yürütmeyi önleyen <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="36c19-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="36c19-111">Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="36c19-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="36c19-112">Serileştirme sırasında ve sonrasında özel yöntemler çalıştırma</span><span class="sxs-lookup"><span data-stu-id="36c19-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="36c19-113">En iyi yöntem ve en kolay yolu (.NET Framework sürüm 2,0 ' de kullanıma sunulmuştur), serileştirme sırasında ve sonrasında verileri düzeltmek için kullanılan yöntemlere aşağıdaki öznitelikleri uygular:</span><span class="sxs-lookup"><span data-stu-id="36c19-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="36c19-114">Bu öznitelikler, tür serileştirme ve seri durumdan çıkarma işlemlerinin herhangi birine veya tüm dört aşamaya katılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="36c19-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="36c19-115">Öznitelikler, her aşamada çağrılması gereken türün yöntemlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="36c19-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="36c19-116">Yöntemler serileştirme akışına erişemez ancak bunun yerine, serileştirme veya sonrasında nesneyi, Serileştirmeden önce ve sonra ve serisini kaldırmadan önce ve sonra değiştirmeniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="36c19-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="36c19-117">Öznitelikler, tür devralma hiyerarşisinin tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide temel alınan en fazla türetilmiş öğesine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="36c19-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="36c19-118">Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi.</span><span class="sxs-lookup"><span data-stu-id="36c19-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="36c19-119">Buna ek olarak, bu mekanizma, Biçimlendiriciler 'nın alanların ve seri hale getirme akışından alımı yok saymasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="36c19-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="36c19-120">Serileştirme ve seri durumdan çıkarmayı denetleme ayrıntıları ve örnekleri için önceki bağlantılardan herhangi birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36c19-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="36c19-121">Ayrıca, var olan bir serileştirilebilir türe yeni bir alan eklerken, <xref:System.Runtime.Serialization.OptionalFieldAttribute> özniteliğini alana uygulayın.</span><span class="sxs-lookup"><span data-stu-id="36c19-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="36c19-122">Yeni alan eksik bir akış işlendiğinde <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> alanın yokluğunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="36c19-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="36c19-123">ISerializable arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="36c19-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="36c19-124">Serileştirme denetiminin diğer yolu, bir nesne üzerinde <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="36c19-125">Ancak, önceki bölümdeki yöntemin serileştirme denetlemek için bu yöntemin yerini almıştır.</span><span class="sxs-lookup"><span data-stu-id="36c19-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="36c19-126">Ayrıca, [seri hale getirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenmiş bir sınıfta varsayılan serileştirme kullanmamalısınız ve sınıf düzeyinde ya da oluşturucuları üzerinde bildirim veya kesinlik güvenliği vardır.</span><span class="sxs-lookup"><span data-stu-id="36c19-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="36c19-127">Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="36c19-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="36c19-128"><xref:System.Runtime.Serialization.ISerializable> uygulamak, `GetObjectData` yönteminin ve nesne seri durumdan çıkarıldığınızda kullanılan özel bir oluşturucunun uygulanması içerir.</span><span class="sxs-lookup"><span data-stu-id="36c19-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="36c19-129">Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="36c19-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
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
  
 <span data-ttu-id="36c19-130">Serileştirme işlemi sırasında **GetObjectData** çağrıldığında, yöntem çağrısıyla verilen <xref:System.Runtime.Serialization.SerializationInfo> doldurmaktan siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="36c19-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="36c19-131">Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36c19-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="36c19-132">Herhangi bir metin adı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-132">Any text can be used as the name.</span></span> <span data-ttu-id="36c19-133">Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla.</span><span class="sxs-lookup"><span data-stu-id="36c19-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="36c19-134">Türetilmiş sınıflar, <xref:System.Runtime.Serialization.ISerializable>ikinci uygularsa, temel nesnede **GetObjectData** yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36c19-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="36c19-135">Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36c19-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="36c19-136">Bu nedenle, serileştirme gerçekleştiren kod, belirtilen <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="36c19-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="36c19-137">Varsayılan ilke altında, bu izin Internet 'Ten indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="36c19-138">**GetObjectData** yöntemi, belirtilen <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağıyla veya özellikle özel verileri korumaya yardımcı olan diğer izinler için gerekli olan [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) 'ı kesin olarak korumalı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36c19-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="36c19-139">Özel bir alan gizli bilgileri depoluyorsa, verileri korumak için **GetObjectData** üzerinde uygun izinleri talep etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="36c19-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="36c19-140">Belirtilen **SerializationFormatter** bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) verilen kodun özel alanlarda depolanan verileri görüntüleyip değiştireabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36c19-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="36c19-141">Bu [SecurityPermission izni](xref:System.Security.Permissions.SecurityPermissionAttribute) verilen kötü niyetli bir çağıran, gizli dizin konumları gibi verileri görüntüleyebilir veya izinler verebilir ve bilgisayardaki bir güvenlik açığından yararlanmak için verileri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="36c19-142">Belirtebileceğiniz güvenlik izni bayraklarının tüm listesi için bkz. [SecurityPermissionFlag numaralandırması](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="36c19-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="36c19-143"><xref:System.Runtime.Serialization.ISerializable> bir sınıfa eklendiğinde, hem **GetObjectData** hem de özel oluşturucuyu uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="36c19-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="36c19-144">**GetObjectData** eksik olduğunda derleyici sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="36c19-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="36c19-145">Ancak, bir oluşturucunun uygulanmasını zorlamak imkansız olduğundan, Oluşturucu yoksa bir uyarı sağlanmaz ve bir sınıfın Oluşturucusu olmadan serisini kaldırma girişimi yapıldığında bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="36c19-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="36c19-146">Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36c19-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="36c19-147">Örneğin, bir arabirimin parçası olarak tanımlanmışsa bir `SetObjectData` yöntemi ortak olmalıdır; Böylece kullanıcılar, **SetObjectData** yönteminin birden çok kez çağrıldığından savunmak için kod yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36c19-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="36c19-148">Aksi halde, bir işlemi yürütme işlemindeki bir nesne üzerinde **SetObjectData** yöntemini çağıran kötü amaçlı bir uygulama olası sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="36c19-149">Seri durumdan çıkarma sırasında, bu amaçla verilen Oluşturucu kullanılarak sınıfa <xref:System.Runtime.Serialization.SerializationInfo> geçirilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="36c19-150">Oluşturucuya yerleştirilmiş tüm Görünürlük kısıtlamaları, nesne seri durumdan çıkarıldığı zaman yok sayılır; Bu nedenle, sınıfı ortak, korumalı, iç veya özel olarak işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c19-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="36c19-151">Ancak, sınıf mühürlenmedikçe oluşturucunun korunmasını sağlamak en iyi uygulamadır, bu durumda oluşturucunun özel olarak işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36c19-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="36c19-152">Oluşturucu Ayrıca kapsamlı giriş doğrulaması da gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="36c19-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="36c19-153">Kötü amaçlı kodun kötüye kullanılmasına engel olmak için, Oluşturucu, başka bir Oluşturucu kullanarak sınıfın bir örneğini almak için gereken güvenlik denetimlerini ve izinlerini zorunlu kılmaz.</span><span class="sxs-lookup"><span data-stu-id="36c19-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="36c19-154">Bu öneriyi izlemeden, kötü amaçlı kod bir nesneyi ön seri hale getirmek için, belirtilen <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağıyla [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile denetim elde edebilir ve bir ortak Oluşturucu kullanılarak standart örnek oluşturma sırasında uygulanan güvenliği atlayarak bir istemci bilgisayardaki nesne serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="36c19-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="36c19-155">Nesnenin durumunu geri yüklemek için, serileştirme sırasında kullanılan adları kullanarak <xref:System.Runtime.Serialization.SerializationInfo> değişkenlerin değerlerini almanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="36c19-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="36c19-156">Temel sınıf <xref:System.Runtime.Serialization.ISerializable>uygularsa, temel oluşturucunun değişkenlerini geri yüklemelerine izin vermek için temel Oluşturucu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36c19-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="36c19-157"><xref:System.Runtime.Serialization.ISerializable>uygulayan bir sınıftan yeni bir sınıf türettiğinizde, türetilmiş sınıf hem oluşturucuyu hem de serileştirilmesi gereken değişkenlere sahipse **GetObjectData** yöntemini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="36c19-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="36c19-158">Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="36c19-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
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
  
 <span data-ttu-id="36c19-159">Seri kaldırma oluşturucusunda temel sınıfı çağırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36c19-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="36c19-160">Bu yapılmazsa, temel sınıftaki Oluşturucu hiçbir şekilde çağrılmaz ve nesne seri durumdan çıktıktan sonra tam olarak oluşturulmamış olur.</span><span class="sxs-lookup"><span data-stu-id="36c19-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="36c19-161">Nesneler, iç içe içinden yeniden yapılandırılır; ve öğesini kaldırma sırasında çağırma yöntemleri istenmeyen yan etkilere sahip olabilir, çünkü çağrılan yöntemler, Çağrının yapıldığı zaman serisi kaldırılan nesne başvurularına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="36c19-162">Seri durumdan çıkarılan sınıf <xref:System.Runtime.Serialization.IDeserializationCallback>uygularsa, nesne grafiğinin tamamı seri durumdan çıkarılmışsa <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> yöntemi otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="36c19-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="36c19-163">Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="36c19-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="36c19-164">Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="36c19-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="36c19-165">Seri durumdan çıkarma sırasında anahtar ve değer çiftlerini almak kolaydır, ancak karma tablodan türetilmiş sınıfların seri durumdan çıkarıldığından emin olmadığı için bu nesneleri karma tabloya geri eklemek sorunlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="36c19-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="36c19-166">Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.</span><span class="sxs-lookup"><span data-stu-id="36c19-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c19-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c19-167">See also</span></span>

- [<span data-ttu-id="36c19-168">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="36c19-168">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="36c19-169">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="36c19-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="36c19-170">Güvenlik ve serileştirme</span><span class="sxs-lookup"><span data-stu-id="36c19-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
