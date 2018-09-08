---
title: 'Arayan bilgileri (F #)'
description: Bir yöntemi arayan bilgileri almak için çağırıcı bilgisi bağımsız değişken öznitelikleri kullanmayı açıklar.
ms.date: 04/25/2017
ms.openlocfilehash: 0f2f4b16804d9156d234cc29d1f72ebe80a5b556
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185491"
---
# <a name="caller-information"></a><span data-ttu-id="d524f-103">Arayan bilgileri</span><span class="sxs-lookup"><span data-stu-id="d524f-103">Caller information</span></span>

<span data-ttu-id="d524f-104">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d524f-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="d524f-105">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d524f-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="d524f-106">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d524f-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="d524f-107">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d524f-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="d524f-108">Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanı:</span><span class="sxs-lookup"><span data-stu-id="d524f-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="d524f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d524f-109">Attribute</span></span>|<span data-ttu-id="d524f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d524f-110">Description</span></span>|<span data-ttu-id="d524f-111">Tür</span><span class="sxs-lookup"><span data-stu-id="d524f-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="d524f-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="d524f-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="d524f-113">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="d524f-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="d524f-114">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="d524f-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="d524f-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="d524f-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="d524f-116">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="d524f-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="d524f-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="d524f-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="d524f-118">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="d524f-118">Method or property name of the caller.</span></span> <span data-ttu-id="d524f-119">Bu konunun ilerleyen bölümlerinde üye adları bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d524f-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="d524f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d524f-120">Example</span></span>

<span data-ttu-id="d524f-121">Aşağıdaki örnek, çağıran izlemek için bu öznitelikler nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d524f-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="d524f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d524f-122">Remarks</span></span>

<span data-ttu-id="d524f-123">Arayan bilgileri öznitelikleri yalnızca isteğe bağlı parametrelere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d524f-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="d524f-124">İsteğe bağlı her parametre için açık bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d524f-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="d524f-125">Arayan bilgisi öznitelikleri arayan bilgisi özniteliği ile donatılmış her isteğe bağlı parametre için uygun değeri yazmak derleyicinin neden.</span><span class="sxs-lookup"><span data-stu-id="d524f-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="d524f-126">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="d524f-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="d524f-127">Tersine sonuçlar [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özelliği için özel durumlar, sonuçlar gizlemeden etkilenmez etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d524f-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="d524f-128">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d524f-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="d524f-129">Üye adları</span><span class="sxs-lookup"><span data-stu-id="d524f-129">Member names</span></span>

<span data-ttu-id="d524f-130">Kullanabileceğiniz [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) üye adı olarak belirtmekten kaçınmak için öznitelik bir `String` çağrılan yöntemin bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="d524f-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="d524f-131">Bu tekniği kullanarak, yeniden adlandırma düzenlemesi değişmeyen ilişkin sorunu önleyebilirsiniz `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d524f-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="d524f-132">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="d524f-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="d524f-133">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="d524f-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="d524f-134">Uygulama [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) veri bağlama sırasında arabirim.</span><span class="sxs-lookup"><span data-stu-id="d524f-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="d524f-135">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d524f-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="d524f-136">Olmadan [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) öznitelik, özellik adını değişmez değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d524f-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="d524f-137">Aşağıdaki grafik üyesi CallerMemberName özniteliğini kullandığınızda döndürülen adlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d524f-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="d524f-138">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="d524f-138">Calls occurs within</span></span>|<span data-ttu-id="d524f-139">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="d524f-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="d524f-140">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="d524f-140">Method, property, or event</span></span>|<span data-ttu-id="d524f-141">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="d524f-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="d524f-142">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="d524f-142">Constructor</span></span>|<span data-ttu-id="d524f-143">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="d524f-143">The string ".ctor"</span></span>|
|<span data-ttu-id="d524f-144">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="d524f-144">Static constructor</span></span>|<span data-ttu-id="d524f-145">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="d524f-145">The string ".cctor"</span></span>|
|<span data-ttu-id="d524f-146">Yok edici</span><span class="sxs-lookup"><span data-stu-id="d524f-146">Destructor</span></span>|<span data-ttu-id="d524f-147">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="d524f-147">The string "Finalize"</span></span>|
|<span data-ttu-id="d524f-148">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d524f-148">User-defined operators or conversions</span></span>|<span data-ttu-id="d524f-149">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="d524f-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="d524f-150">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="d524f-150">Attribute constructor</span></span>|<span data-ttu-id="d524f-151">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="d524f-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="d524f-152">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="d524f-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="d524f-153">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="d524f-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="d524f-154">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="d524f-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d524f-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d524f-155">See also</span></span>

- [<span data-ttu-id="d524f-156">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d524f-156">Attributes</span></span>](attributes.md)  
- [<span data-ttu-id="d524f-157">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d524f-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
- [<span data-ttu-id="d524f-158">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="d524f-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
