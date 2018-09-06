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
ms.openlocfilehash: 6151bf670a455d4c9862e80fd06314e4e1621080
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881921"
---
# <a name="custom-serialization"></a><span data-ttu-id="21074-102">Özel serileştirme</span><span class="sxs-lookup"><span data-stu-id="21074-102">Custom serialization</span></span>
<span data-ttu-id="21074-103">Özel seri hale getirme serileştirme ve seri durumundan çıkarma bir türün denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="21074-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="21074-104">Serileştirme denetleyerek, türü çekirdek işlevselliğini bozucu olmayan bir tür sürümleri arasında seri hale getrime ve yeteneği olan serileştirme uyumluluğu sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="21074-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="21074-105">Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan.</span><span class="sxs-lookup"><span data-stu-id="21074-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="21074-106">Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir.</span><span class="sxs-lookup"><span data-stu-id="21074-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="21074-107">Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="21074-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="21074-108">Aşağıdaki bölümler serileştirme denetlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="21074-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  <span data-ttu-id="21074-109">.NET Framework 4.0 önceki sürümlerinde, özel kullanıcı veri kısmen güvenilen bir derleme serileştirme GetObjectData kullanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="21074-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="21074-110">Yöntem ile işaretlenmiş bir sürüm 4.0, başlayarak <xref:System.Security.SecurityCriticalAttribute> kısmen güvenilen derlemelerde yürütme önleyen özniteliği.</span><span class="sxs-lookup"><span data-stu-id="21074-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="21074-111">Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21074-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="21074-112">Özel yöntemlerini sırasında ve sonra serileştirme çalıştıran</span><span class="sxs-lookup"><span data-stu-id="21074-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="21074-113">En iyi yöntem ve (.NET Framework'ün 2.0 sürümünde sunulan) kolay yolu olan aşağıdaki öznitelikler sırasında ve seri hale getirme sonra veri düzeltmek için kullanılan yöntemleri uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="21074-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="21074-114">Bu öznitelikler herhangi birinin veya tüm dört serileştirme ve seri durumundan çıkarma işlemlerinin aşamadan katılmak türüne izin verin.</span><span class="sxs-lookup"><span data-stu-id="21074-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="21074-115">Öznitelikleri yöntemleri her aşamada çağrılmalıdır türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="21074-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="21074-116">Yöntemleri seri hale getirme akışı erişim değil ancak bunun yerine nesne önce ve seri hale getirme, veya önce ve sonra seri durumundan çıkarma alter izin.</span><span class="sxs-lookup"><span data-stu-id="21074-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="21074-117">Öznitelikleri türü devralma hiyerarşisinin tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide temel en türetilen çağrılır.</span><span class="sxs-lookup"><span data-stu-id="21074-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="21074-118">Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21074-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="21074-119">Ayrıca, bu mekanizma alanları ve seri hale getirme akışı almanın popülasyonu yok sayılacak biçimlendiricileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="21074-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="21074-120">Ayrıntıları ve örnekleri serileştirme ve seri durumundan çıkarma denetlemek için önceki bağlantılardan herhangi birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="21074-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="21074-121">Ayrıca, yeni bir alan varolan serializable bir tür eklerken uygulamak <xref:System.Runtime.Serialization.OptionalFieldAttribute> alanına öznitelik.</span><span class="sxs-lookup"><span data-stu-id="21074-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="21074-122"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yeni alan eksik olan bir akış işlendiğinde alan olmaması yok sayar.</span><span class="sxs-lookup"><span data-stu-id="21074-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="21074-123">ISerializable arabirimini uygulayan</span><span class="sxs-lookup"><span data-stu-id="21074-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="21074-124">Serileştirme denetlemek için başka bir şekilde uygulayarak sağlanır <xref:System.Runtime.Serialization.ISerializable> arabirimdeki bir nesne.</span><span class="sxs-lookup"><span data-stu-id="21074-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="21074-125">Ancak, önceki bölümde yöntem Denetim serileştirme için bu yöntem yerine geçer unutmayın.</span><span class="sxs-lookup"><span data-stu-id="21074-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="21074-126">Ayrıca, varsayılan seri hale getirme ile işaretlenmiş bir sınıfındaki kullanmamalısınız [Serializable](xref:System.SerializableAttribute) öznitelik ve bildirim temelli veya kesinlik temelli güvenlik sınıf düzeyinde veya kendi oluşturucular sahiptir.</span><span class="sxs-lookup"><span data-stu-id="21074-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="21074-127">Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21074-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="21074-128">Uygulama <xref:System.Runtime.Serialization.ISerializable> uygulayan içerir `GetObjectData` yöntemi ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="21074-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="21074-129">Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21074-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
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
  
 <span data-ttu-id="21074-130">Zaman **GetObjectData** çağrılır serileştirme sırasında hesaplarla için sorumlu olduğunuz <xref:System.Runtime.Serialization.SerializationInfo> yöntem çağrısının ile sağlanan.</span><span class="sxs-lookup"><span data-stu-id="21074-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="21074-131">Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21074-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="21074-132">Herhangi bir metin adı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21074-132">Any text can be used as the name.</span></span> <span data-ttu-id="21074-133">Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla.</span><span class="sxs-lookup"><span data-stu-id="21074-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="21074-134">Türetilen sınıfların çağrısı **GetObjectData** temel nesnesi üzerinde yöntemi, ikinci uygular <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="21074-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="21074-135">Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="21074-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="21074-136">Bu nedenle, serileştirme gerçekleştiren kod gerektirir [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="21074-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="21074-137">Varsayılan ilkesi altında çok Internet karşıdan bu izin verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="21074-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="21074-138">**GetObjectData** yöntemi açıkça korunmalıdır ya da göre zorlu [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> göre özellikle yardımcı olan diğer izinler yoğun ya da belirtilen bayrağı özel verileri koruyun.</span><span class="sxs-lookup"><span data-stu-id="21074-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="21074-139">Özel bir alan duyarlı bilgi içermiyorsa, üzerinde uygun izinleri talep **GetObjectData** verileri korumak için.</span><span class="sxs-lookup"><span data-stu-id="21074-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="21074-140">Verilmiş kodun [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile **SerializationFormatter** belirtilen bayrağı görüntüleyebilir ve özel alanları depolanan verileri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21074-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="21074-141">Kötü amaçlı bir arayan bu verilen [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gizli dizin konumları veya izin verilenler gibi veri görüntüleyebilir ve bilgisayardaki güvenlik açığı verileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="21074-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="21074-142">Güvenlik izni bayrakları belirtebilirsiniz tam listesi için bkz. [SecurityPermissionFlag numaralandırma](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="21074-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="21074-143">Olduğunda vurgulamak önemlidir <xref:System.Runtime.Serialization.ISerializable> için bir sınıf her ikisi de uygulanmalı eklenir **GetObjectData** ve özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="21074-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="21074-144">Varsa derleyici sizi uyarır **GetObjectData** eksik.</span><span class="sxs-lookup"><span data-stu-id="21074-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="21074-145">Ancak, bir kurucu uygulanması zorlamak olanaksız olduğundan, hiçbir uyarı oluşturucu yok ve bir sınıf oluşturucu olmadan serisini kaldırmak için girişiminde bulunulduğunda bir özel durum için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="21074-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="21074-146">Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21074-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="21074-147">Örneğin, bir `SetObjectData` yöntemi bir arabirim bir parçası olarak tanımlanmışsa ortak olmalıdır; böylece kullanıcılar sahip karşı korumaya için kod yazmanız gereken **SetObjectData** yöntemi birden çok kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="21074-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="21074-148">Aksi takdirde, kötü amaçlı bir uygulamayı çağırır **SetObjectData** yöntemi bir işlem yürütülürken sürecinde bir nesne üzerinde olası sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="21074-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="21074-149">Seri durumundan çıkarma sırasında <xref:System.Runtime.Serialization.SerializationInfo> bu amaç için sağlanan oluşturucu kullanılarak sınıfına geçirilen.</span><span class="sxs-lookup"><span data-stu-id="21074-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="21074-150">Nesnenin seri durumda olduğunda Oluşturucu tüm görünürlük kısıtlamaları göz ardı edilir; Bu nedenle ortak, korumalı, dahili veya özel olarak sınıf işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21074-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="21074-151">Ancak, sınıf, bu durumda oluşturucu özel işaretlenmelidir korumalı olup sürece korumalı Oluşturucu olun en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="21074-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="21074-152">Oluşturucuya, ayrıca kapsamlı giriş doğrulaması gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21074-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="21074-153">Kötü amaçlı kod tarafından kötüye kaçınmak için oluşturucuya aynı güvenlik denetimleri ve diğer bir oluşturucu kullanılarak sınıfının bir örneği elde etmek için gereken izinler uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="21074-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="21074-154">Bu öneri uygulamazsanız, kötü amaçlı kod bir nesne preserialize, denetimi ile elde [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilen ve atlama herhangi bir istemci bilgisayarında bir nesneyi seri durumdan çıkarma Standart örnek oluşturma sırasında bir Genel oluşturucu kullanılarak uygulanmış güvenlik.</span><span class="sxs-lookup"><span data-stu-id="21074-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="21074-155">Nesne durumunu geri yüklemek için basitçe değişkenlerin değerlerini alma <xref:System.Runtime.Serialization.SerializationInfo> serileştirme sırasında kullanılan adları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="21074-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="21074-156">Temel sınıfı kullanılıyorsa <xref:System.Runtime.Serialization.ISerializable>, temel oluşturucuyu değişkenlerini geri yüklemek temel nesne izin vermek için çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21074-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="21074-157">Olduğunda, türetilen yeni bir sınıf uygulayan birinden <xref:System.Runtime.Serialization.ISerializable>, türetilmiş sınıf oluşturucu her iki uygulamalıdır yanı sıra **GetObjectData** seri hale gerek değişkenleri varsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21074-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="21074-158">Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21074-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
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
  
 <span data-ttu-id="21074-159">Temel sınıfı seri durumundan çıkarma oluşturucuda çağrılacak unutmayın.</span><span class="sxs-lookup"><span data-stu-id="21074-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="21074-160">Bu işlem değil, temel sınıfı Oluşturucu hiçbir zaman çağrılır ve nesne tam olarak seri durumundan çıkarma sonra oluşturulur değil.</span><span class="sxs-lookup"><span data-stu-id="21074-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="21074-161">Nesneleri içinden yeniden; ve arama yöntemleri seri durumundan çıkarma sırasında çağrılır yöntemleri için çağrı yapılır zaman serisi değil nesne başvurularını başvurabilir olduğundan istenmeyen yan etkileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="21074-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="21074-162">Sınıf olan uygular seri durumdan <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> yöntemi tüm nesne grafiğinin seri olduğunda otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="21074-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="21074-163">Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="21074-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="21074-164">Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="21074-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="21074-165">Anahtar ve değer çiftleri seri durumundan çıkarma sırasında almak kolaydır, ancak bu nesnelerine geri karma tablo sorunlara neden olabilir karma tablosundan türetilmiş bu sınıfları garanti olduğundan ekleme seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="21074-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="21074-166">Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.</span><span class="sxs-lookup"><span data-stu-id="21074-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21074-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21074-167">See also</span></span>

- [<span data-ttu-id="21074-168">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="21074-168">Binary Serialization</span></span>](binary-serialization.md)  
- [<span data-ttu-id="21074-169">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="21074-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
- [<span data-ttu-id="21074-170">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="21074-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
