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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5718f19318121c2025b9d92a5947574289c1f4d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="custom-serialization"></a><span data-ttu-id="79437-102">Özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="79437-102">Custom serialization</span></span>
<span data-ttu-id="79437-103">Özel serileştirme seri hale getirme ve seri durumdan çıkarma türü denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="79437-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="79437-104">Seri hale getirme denetleyerek, seri hale getirmek ve seri durumdan türü çekirdek işlevselliğini çiğnemekten olmadan bir türü sürümleri arasında özelliği seri hale getirme uyumluluğundan emin olmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="79437-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="79437-105">Örneğin, bir tür ilk sürümü olabilir yalnızca iki alan.</span><span class="sxs-lookup"><span data-stu-id="79437-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="79437-106">Sonraki sürümünde bir tür, pek çok daha fazla alan eklenir.</span><span class="sxs-lookup"><span data-stu-id="79437-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="79437-107">Henüz bir uygulamanın ikinci sürümü seri hale getirmek ve her iki türü seri durumdan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79437-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="79437-108">Aşağıdaki bölümlerde serileştirme denetleme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79437-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  <span data-ttu-id="79437-109">.NET Framework 4.0 önceki sürümlerde, kısmen güvenilir bir derleme özel kullanıcı verilerini serileştirmek GetObjectData kullanarak gerçekleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="79437-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="79437-110">Yöntem ile işaretlenmiş sürüm 4.0 başlayarak <xref:System.Security.SecurityCriticalAttribute> , kısmen güvenilir derlemeler yürütmeyi engelleyen özniteliği.</span><span class="sxs-lookup"><span data-stu-id="79437-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="79437-111">Bu durum çalışmak için uygulayan <xref:System.Runtime.Serialization.ISafeSerializationData> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="79437-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="79437-112">Çalışmakta olan özel yöntemler sırasında ve sonrasında seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="79437-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="79437-113">En iyi uygulama ve en kolay yolu (.NET Framework 2.0 sürümünde sunulan) olan aşağıdaki öznitelikler veri sırasında ve sonrasında serileştirme düzeltmek için kullanılan yöntemleri uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="79437-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="79437-114">Özniteliklerden herhangi birinin veya tüm dört aşamaları seri hale getirme ve seri durumdan çıkarma işlemleri katılmayı türüne izin verme.</span><span class="sxs-lookup"><span data-stu-id="79437-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="79437-115">Öznitelikleri her aşaması sırasında çağrılması gereken türü yöntemleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="79437-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="79437-116">Yöntem serileştirme akış erişmemesi ancak bunun yerine önce ve seri hale getirme, veya önce ve sonra seri durumdan çıkarma nesnesi alter izin verir.</span><span class="sxs-lookup"><span data-stu-id="79437-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="79437-117">Öznitelikleri türü Devralma Hiyerarşisi tüm düzeylerinde uygulanabilir ve her yöntem hiyerarşide taban en çok türetilen çağrılır.</span><span class="sxs-lookup"><span data-stu-id="79437-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="79437-118">Bu mekanizma karmaşıklığı ve uygulama ortaya çıkan sorunları kaçınan <xref:System.Runtime.Serialization.ISerializable> serileştirme ve seri durumundan çıkarma en türetilen uygulamaya için sorumluluk vererek arabirimi.</span><span class="sxs-lookup"><span data-stu-id="79437-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="79437-119">Ayrıca, bu mekanizma alanları ve seri hale getirme akış alımı popülasyonunu yoksaymak biçimlendiricileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="79437-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="79437-120">Ayrıntılar ve seri hale getirme ve seri durumdan çıkarma denetleme örnekleri için önceki bağlantılardan birini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="79437-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="79437-121">Ayrıca, yeni bir alan için mevcut bir seri hale getirilebilir türü eklerken, uygulama <xref:System.Runtime.Serialization.OptionalFieldAttribute> alana özniteliği.</span><span class="sxs-lookup"><span data-stu-id="79437-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="79437-122"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yeni alan eksik bir akış işlendiğinde alan yokluğu yok sayar.</span><span class="sxs-lookup"><span data-stu-id="79437-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="79437-123">ISerializable arabirimi uygulama</span><span class="sxs-lookup"><span data-stu-id="79437-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="79437-124">Seri hale getirme denetlemek için diğer bir yol uygulayarak elde edilen <xref:System.Runtime.Serialization.ISerializable> bir nesne üzerinde arabirimi.</span><span class="sxs-lookup"><span data-stu-id="79437-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="79437-125">Ancak, önceki bölümde yöntemi denetim serileştirme için bu yöntem yerini aldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79437-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="79437-126">Ayrıca, varsayılan seri hale getirme ile işaretli bir sınıfını kullanmamalısınız [Serializable](xref:System.SerializableAttribute) özniteliği ve bildirim temelli veya kesinlik temelli güvenliği sınıf düzeyinde veya kendi oluşturucular sahiptir.</span><span class="sxs-lookup"><span data-stu-id="79437-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="79437-127">Bunun yerine, bu sınıflar her zaman uygulamalıdır <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="79437-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="79437-128">Uygulama <xref:System.Runtime.Serialization.ISerializable> uygulama içerir `GetObjectData` yöntemi ve nesnenin seri durumda olduğunda kullanan bir özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="79437-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="79437-129">Aşağıdaki örnek kodu nasıl uygulanacağını gösterir <xref:System.Runtime.Serialization.ISerializable> üzerinde `MyObject` önceki bölümünden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="79437-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
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
  
 <span data-ttu-id="79437-130">Zaman **GetObjectData** çağrılır doldurmak için sorumlu seri hale getirme sırasında <xref:System.Runtime.Serialization.SerializationInfo> yöntemi çağrısı ile sağlanan.</span><span class="sxs-lookup"><span data-stu-id="79437-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="79437-131">Ad ve değer çiftleri olarak seri hale için değişkenlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79437-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="79437-132">Herhangi bir metin adı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79437-132">Any text can be used as the name.</span></span> <span data-ttu-id="79437-133">Hangi üye değişkenleri eklenir karar özgürlüğü sahip <xref:System.Runtime.Serialization.SerializationInfo>, nesne seri durumundan çıkarma sırasında geri yüklemek için yeterli veri serileştirilmiş koşuluyla.</span><span class="sxs-lookup"><span data-stu-id="79437-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="79437-134">Türetilen sınıflar çağrısı **GetObjectData** temel nesnesi üzerinde yöntemi, ikinci uygular <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="79437-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="79437-135">Serileştirme bakın veya erişilemez durumda nesne örneği verileri değiştirmek başka bir kod izin vermek demektir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79437-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="79437-136">Bu nedenle, serileştirme gerçekleştirir kodu gerektirir [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="79437-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="79437-137">Varsayılan ilkesi altında için Internet indirilen bu izni verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="79437-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="79437-138">**GetObjectData** yöntemi açıkça korunmalıdır ya da göre yoğun [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> göre özellikle yardımcı diğer izinler yoğun ya da belirtilen bayrağı özel verileri korur.</span><span class="sxs-lookup"><span data-stu-id="79437-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="79437-139">Özel bir alan gizli bilgileri depoluyorsa, üzerinde uygun izinleri talep **GetObjectData** verileri korumak için.</span><span class="sxs-lookup"><span data-stu-id="79437-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="79437-140">Verildi bu kodu unutmayın [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile **SerializationFormatter** bayrağı belirtilmiş görüntüleyebilir ve özel alanlarında depolanan verilerin değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79437-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="79437-141">Bu kötü amaçlı çağıran verilen [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) gizli dizin konumları veya izin verilenler gibi verileri görüntüleyebilir ve bilgisayardaki güvenlik açığından verileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="79437-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="79437-142">Güvenlik izni bayrakları belirtebilirsiniz tam bir listesi için bkz: [SecurityPermissionFlag numaralandırma](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="79437-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="79437-143">Zaman stres önemlidir <xref:System.Runtime.Serialization.ISerializable> her ikisi de uygulanmalı bir sınıfa eklenen **GetObjectData** ve özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="79437-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="79437-144">Derleyici, sizi uyarır **GetObjectData** eksik.</span><span class="sxs-lookup"><span data-stu-id="79437-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="79437-145">Ancak, bir oluşturucu uyarlamasını gerçekleştirmek imkansız olduğu için hiçbir uyarı oluşturucusu yok ve sınıf oluşturucu olmadan serisini kaldırmak için bir girişimde zaman bir özel durum için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="79437-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="79437-146">Geçerli tasarım yukarıda tercih bir <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> güvenlik ve sürüm olası sorunları almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="79437-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="79437-147">Örneğin, bir `SetObjectData` yöntemi bir arabirim bir parçası olarak tanımlanmışsa ortak olmalıdır; böylece kullanıcıların sahip karşı korumak için kod yazmanız gerekir **SetObjectData** yöntemi birden çok kez çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="79437-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="79437-148">Aksi takdirde, kötü amaçlı bir uygulama, çağıran **SetObjectData** yöntemi bir işlem yürütme sürecinde bir nesne üzerinde olası sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="79437-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="79437-149">Seri durumdan çıkarma sırasında <xref:System.Runtime.Serialization.SerializationInfo> bu amaç için sağlanan Oluşturucusu kullanılarak sınıfı geçirilir.</span><span class="sxs-lookup"><span data-stu-id="79437-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="79437-150">Nesnenin seri durumda olduğunda Oluşturucu yerleştirilen tüm görünürlük kısıtlamaları göz ardı edilir; Bu nedenle sınıf ortak, korumalı, iç veya özel olarak işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79437-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="79437-151">Ancak, sınıf; bu durumda Oluşturucusu özel işaretlenmelidir korumalı olduğu sürece korumalı Oluşturucusu yapmak en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="79437-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="79437-152">Oluşturucusu de kapsamlı giriş doğrulaması gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="79437-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="79437-153">Kötü amaçlı kod tarafından kötüye kullanımı önlemek için aynı güvenlik denetimleri ve diğer oluşturucuyu kullanarak sınıfının bir örneği elde etmek için gereken izinler Oluşturucusu uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="79437-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="79437-154">Bu öneriyi uygulamazsanız kötü amaçlı kod bir nesne preserialize, denetimi ile elde [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> bayrağı belirtilen ve nesnedeki atlayarak herhangi bir istemci bilgisayarda Standart örnek oluşturma sırasında bir public oluşturucuya kullanarak uygulanmış güvenliği.</span><span class="sxs-lookup"><span data-stu-id="79437-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="79437-155">Nesnenin durumunu geri yüklemek için yalnızca değişkenlerin değerleri almak <xref:System.Runtime.Serialization.SerializationInfo> seri hale getirme sırasında kullanılan adları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="79437-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="79437-156">Taban sınıfı uyguluyorsa <xref:System.Runtime.Serialization.ISerializable>, temel oluşturucuyu değişkenlerini geri yüklemek temel nesne izin vermek için çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79437-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="79437-157">Ne zaman, türetilen yeni bir sınıf uygulayan bir <xref:System.Runtime.Serialization.ISerializable>, türetilen sınıfın iki Oluşturucusu uygulamalıdır yanı sıra **GetObjectData** serileştirilmesi gereken değişkenleri varsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="79437-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="79437-158">Aşağıdaki kod örneğinde nasıl yapıldığını gösterir kullanarak `MyObject` daha önce gösterilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="79437-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
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
  
 <span data-ttu-id="79437-159">Seri durumdan çıkarma Oluşturucusu çağrı temel sınıfı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79437-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="79437-160">Bu yapılır değil, temel sınıf oluşturucu hiçbir zaman denir ve nesne tamamen seri durumdan çıkarma sonra oluşturulan değil.</span><span class="sxs-lookup"><span data-stu-id="79437-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="79437-161">Nesneleri, içinden yeniden; ve çağrılan yöntemler çağrıyı yapan zaman serisi değil nesne başvuruları başvurmak çünkü seri durumdan çıkarma sırasında çağıran yöntemleri istenmeyen yan etkileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="79437-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="79437-162">Sınıf olan Implements çıkarıldıysa <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> yöntemi tüm nesne grafiğinin seri durumdan olduğunda otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="79437-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="79437-163">Bu noktada, başvurulan tüm alt nesneleri tam olarak geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="79437-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="79437-164">Karma tablo olay dinleyicisi kullanmadan seri durumdan zor bir sınıfı tipik bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="79437-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="79437-165">Seri durumdan çıkarma sırasında anahtar ve değer çiftleri almak kolaydır, ancak bu nesneleri geri karma tablosu için sorunlara neden olabilir karma tablosundan türetilmiş bu sınıfları garanti olduğundan ekleme seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="79437-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="79437-166">Bu aşamada karma tablo üzerinde yöntemleri çağırmak bu nedenle önerilir değil.</span><span class="sxs-lookup"><span data-stu-id="79437-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79437-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79437-167">See also</span></span>  
 [<span data-ttu-id="79437-168">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="79437-168">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="79437-169">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="79437-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="79437-170">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="79437-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
