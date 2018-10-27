---
title: Arayan bilgileri (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4a0e4d6ecad1863832a33ba91485d0c12675cd57
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185280"
---
# <a name="caller-information-c"></a><span data-ttu-id="3bfc9-102">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="3bfc9-102">Caller Information (C#)</span></span>

<span data-ttu-id="3bfc9-103">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="3bfc9-104">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="3bfc9-105">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="3bfc9-106">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="3bfc9-107">Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="3bfc9-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="3bfc9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3bfc9-108">Attribute</span></span>|<span data-ttu-id="3bfc9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bfc9-109">Description</span></span>|<span data-ttu-id="3bfc9-110">Tür</span><span class="sxs-lookup"><span data-stu-id="3bfc9-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="3bfc9-111">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="3bfc9-112">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="3bfc9-113">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="3bfc9-114">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-114">Method or property name of the caller.</span></span> <span data-ttu-id="3bfc9-115">Bkz: [üye adları](#member-names) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="3bfc9-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bfc9-116">Example</span></span>

<span data-ttu-id="3bfc9-117">Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="3bfc9-118">Her çağrıda `TraceMessage` yöntemi arayan bilgileri isteğe bağlı parametrelerin bağımsız değişkenleri olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="3bfc9-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bfc9-119">Remarks</span></span>

<span data-ttu-id="3bfc9-120">Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="3bfc9-121">İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="3bfc9-122">Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="3bfc9-123">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="3bfc9-124">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="3bfc9-125">Tersine sonuçlar <xref:System.Exception.StackTrace%2A> özelliği için özel durumlar, sonuçlar gizlemeden etkilenmez etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="3bfc9-126">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="3bfc9-127">Üye adları</span><span class="sxs-lookup"><span data-stu-id="3bfc9-127">Member names</span></span>

<span data-ttu-id="3bfc9-128">Kullanabileceğiniz `CallerMemberName` üye adı olarak belirtmekten kaçınmak için öznitelik bir `String` çağrılan yöntemin bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="3bfc9-129">Bu tekniği kullanarak, sorundan kaçınmak, **düzenlemeyi yeniden adlandırma** değişmez `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="3bfc9-130">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="3bfc9-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="3bfc9-131">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="3bfc9-132">Uygulama <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama sırasında arabirim.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="3bfc9-133">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="3bfc9-134">Olmadan `CallerMemberName` öznitelik, özellik adını değişmez değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="3bfc9-135">Aşağıdaki grafik üyesi kullandığınızda döndürülen adlarını gösterir. `CallerMemberName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="3bfc9-136">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="3bfc9-136">Calls occurs within</span></span>|<span data-ttu-id="3bfc9-137">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="3bfc9-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="3bfc9-138">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="3bfc9-138">Method, property, or event</span></span>|<span data-ttu-id="3bfc9-139">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="3bfc9-140">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="3bfc9-140">Constructor</span></span>|<span data-ttu-id="3bfc9-141">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="3bfc9-141">The string ".ctor"</span></span>|
|<span data-ttu-id="3bfc9-142">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="3bfc9-142">Static constructor</span></span>|<span data-ttu-id="3bfc9-143">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="3bfc9-143">The string ".cctor"</span></span>|
|<span data-ttu-id="3bfc9-144">Yok edici</span><span class="sxs-lookup"><span data-stu-id="3bfc9-144">Destructor</span></span>|<span data-ttu-id="3bfc9-145">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="3bfc9-145">The string "Finalize"</span></span>|
|<span data-ttu-id="3bfc9-146">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="3bfc9-146">User-defined operators or conversions</span></span>|<span data-ttu-id="3bfc9-147">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="3bfc9-148">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="3bfc9-148">Attribute constructor</span></span>|<span data-ttu-id="3bfc9-149">Yöntem veya öznitelik uygulandığı özellik adı.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="3bfc9-150">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="3bfc9-151">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="3bfc9-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="3bfc9-152">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3bfc9-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bfc9-153">See also</span></span>

- [<span data-ttu-id="3bfc9-154">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="3bfc9-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="3bfc9-155">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="3bfc9-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="3bfc9-156">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3bfc9-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="3bfc9-157">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="3bfc9-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
