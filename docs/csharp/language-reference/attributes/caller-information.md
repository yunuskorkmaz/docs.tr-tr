---
title: 'C# Ayrılmış öznitelikler: Arayan bilgilerini izleme'
ms.date: 04/09/2020
description: Bu öznitelikler derleyiciye üye çağıran kod hakkında bilgi oluşturmasını bildirir. Ayrıntılı izleme bilgileri sağlamak için CallerFilePath, CallerLineNumber ve CallerMemberName'yi kullanıyorsunuz
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389879"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="569d8-104">Ayrılmış öznitelikler: Arayan bilgilerini belirleme</span><span class="sxs-lookup"><span data-stu-id="569d8-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="569d8-105">Bilgi özniteliklerini kullanarak, bir yönteme arayan hakkında bilgi elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569d8-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="569d8-106">Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569d8-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="569d8-107">Üye arayan bilgilerini elde etmek için isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="569d8-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="569d8-108">Her isteğe bağlı parametre varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="569d8-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="569d8-109">Aşağıdaki <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> tabloda, ad alanında tanımlanan Arayan Bilgileri öznitelikleri listelenir:</span><span class="sxs-lookup"><span data-stu-id="569d8-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="569d8-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="569d8-110">Attribute</span></span>|<span data-ttu-id="569d8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="569d8-111">Description</span></span>|<span data-ttu-id="569d8-112">Tür</span><span class="sxs-lookup"><span data-stu-id="569d8-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="569d8-113">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="569d8-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="569d8-114">Tam yol derleme zamanda ki yoldur.</span><span class="sxs-lookup"><span data-stu-id="569d8-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="569d8-115">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="569d8-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="569d8-116">Arayanın yöntem adı veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="569d8-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="569d8-117">Bu bilgiler, izleme, hata ayıklama yazmanıza ve tanılama araçları oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="569d8-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="569d8-118">Aşağıdaki örnek, arayan bilgileri özniteliklerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="569d8-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="569d8-119">`TraceMessage` Yönteme yapılan her çağrıda, arayan bilgileri isteğe bağlı parametrelere bağımsız değişken olarak ikame edilir.</span><span class="sxs-lookup"><span data-stu-id="569d8-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="569d8-120">Her isteğe bağlı parametre için açık bir varsayılan değer belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569d8-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="569d8-121">Arayan bilgi özniteliklerini isteğe bağlı olarak belirtilmeyen parametrelere uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="569d8-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="569d8-122">Arayan bilgi öznitelikleri bir parametre isteğe bağlı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="569d8-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="569d8-123">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="569d8-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="569d8-124">Arayan bilgi değerleri derleme zamanında Ara Dile (IL) edebi olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="569d8-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="569d8-125"><xref:System.Exception.StackTrace%2A> Özel durumlar için özelliğin sonuçlarının aksine, sonuçlar gizlemeden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="569d8-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="569d8-126">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569d8-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="569d8-127">Üye adları</span><span class="sxs-lookup"><span data-stu-id="569d8-127">Member names</span></span>

<span data-ttu-id="569d8-128">Özniteliği, `CallerMemberName` üye adı niçin çağrılması `String` metoduna bağımsız değişken olarak belirtmemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569d8-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="569d8-129">Bu tekniği kullanarak, **Yeniden Adlandırma Değerlerini** değiştirmez `String` sorunu önlemek.</span><span class="sxs-lookup"><span data-stu-id="569d8-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="569d8-130">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="569d8-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="569d8-131">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="569d8-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="569d8-132">Verileri bağlarken <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="569d8-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="569d8-133">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="569d8-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="569d8-134">`CallerMemberName` Öznitelik olmadan, özellik adını gerçek olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="569d8-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="569d8-135">Aşağıdaki grafik, özniteliği kullandığınızda `CallerMemberName` döndürülen üye adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="569d8-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="569d8-136">Aramalar içinde oluşur</span><span class="sxs-lookup"><span data-stu-id="569d8-136">Calls occur within</span></span>|<span data-ttu-id="569d8-137">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="569d8-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="569d8-138">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="569d8-138">Method, property, or event</span></span>|<span data-ttu-id="569d8-139">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="569d8-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="569d8-140">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="569d8-140">Constructor</span></span>|<span data-ttu-id="569d8-141">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="569d8-141">The string ".ctor"</span></span>|
|<span data-ttu-id="569d8-142">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="569d8-142">Static constructor</span></span>|<span data-ttu-id="569d8-143">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="569d8-143">The string ".cctor"</span></span>|
|<span data-ttu-id="569d8-144">Yok edici</span><span class="sxs-lookup"><span data-stu-id="569d8-144">Destructor</span></span>|<span data-ttu-id="569d8-145">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="569d8-145">The string "Finalize"</span></span>|
|<span data-ttu-id="569d8-146">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="569d8-146">User-defined operators or conversions</span></span>|<span data-ttu-id="569d8-147">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="569d8-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="569d8-148">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="569d8-148">Attribute constructor</span></span>|<span data-ttu-id="569d8-149">Özniteliğin uygulandığı yöntemin veya özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="569d8-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="569d8-150">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="569d8-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="569d8-151">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="569d8-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="569d8-152">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="569d8-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="569d8-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="569d8-153">See also</span></span>

- [<span data-ttu-id="569d8-154">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="569d8-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="569d8-155">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="569d8-155">Attributes</span></span>](../../../standard/attributes/index.md)
