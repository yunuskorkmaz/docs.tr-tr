---
title: 'Arayan bilgileri (F #)'
description: Arayan bilgileri bağımsız değişkeni öznitelikleri bir yöntemden arayan bilgileri almak için nasıl kullanılacağını açıklar.
ms.date: 04/25/2017
ms.openlocfilehash: 6fd80213cdaf2c4662fd4c2ed9eaf8949e397efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564811"
---
# <a name="caller-information"></a><span data-ttu-id="b1f2d-103">Arayan bilgileri</span><span class="sxs-lookup"><span data-stu-id="b1f2d-103">Caller information</span></span>

<span data-ttu-id="b1f2d-104">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="b1f2d-105">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="b1f2d-106">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="b1f2d-107">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="b1f2d-108">Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanı:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="b1f2d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1f2d-109">Attribute</span></span>|<span data-ttu-id="b1f2d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f2d-110">Description</span></span>|<span data-ttu-id="b1f2d-111">Tür</span><span class="sxs-lookup"><span data-stu-id="b1f2d-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="b1f2d-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="b1f2d-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="b1f2d-113">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="b1f2d-114">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="b1f2d-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="b1f2d-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="b1f2d-116">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="b1f2d-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="b1f2d-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="b1f2d-118">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-118">Method or property name of the caller.</span></span> <span data-ttu-id="b1f2d-119">Bu konunun ilerleyen bölümlerinde üye adlarının bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="b1f2d-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f2d-120">Example</span></span>

<span data-ttu-id="b1f2d-121">Aşağıdaki örnek, çağıran izlemek için bu öznitelikler nasıl kullanabileceğinize gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-121">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b1f2d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1f2d-122">Remarks</span></span>

<span data-ttu-id="b1f2d-123">Arayan bilgileri öznitelikleri için isteğe bağlı parametreler yalnızca uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="b1f2d-124">Her bir isteğe bağlı parametre için açık bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="b1f2d-125">Arayan bilgileri öznitelikleri arayan bilgileri özniteliği ile donatılmış her isteğe bağlı bir parametre uygun değeri yazmak derleyici neden.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="b1f2d-126">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="b1f2d-127">Sonuçlarını aksine [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özellik için özel durumlar, sonuçları gizleme tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="b1f2d-128">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="b1f2d-129">Üye adlarının</span><span class="sxs-lookup"><span data-stu-id="b1f2d-129">Member names</span></span>

<span data-ttu-id="b1f2d-130">Kullanabileceğiniz [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliği üye adı olarak belirtmekten kaçının bir `String` çağrılan yöntemin bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="b1f2d-131">Bu yöntemi kullanarak, yeniden adlandırma yeniden düzenleme değişmez bir sorunu önlemenize `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="b1f2d-132">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="b1f2d-133">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="b1f2d-134">Uygulama [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) veri bağlama sırasında arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="b1f2d-135">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="b1f2d-136">Olmadan [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) öznitelik, bir hazır değer özellik adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="b1f2d-137">Aşağıdaki grafikte üye CallerMemberName özniteliğini kullandığınızda, döndürülen adlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="b1f2d-138">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="b1f2d-138">Calls occurs within</span></span>|<span data-ttu-id="b1f2d-139">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="b1f2d-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="b1f2d-140">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="b1f2d-140">Method, property, or event</span></span>|<span data-ttu-id="b1f2d-141">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="b1f2d-142">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="b1f2d-142">Constructor</span></span>|<span data-ttu-id="b1f2d-143">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="b1f2d-143">The string ".ctor"</span></span>|
|<span data-ttu-id="b1f2d-144">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="b1f2d-144">Static constructor</span></span>|<span data-ttu-id="b1f2d-145">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="b1f2d-145">The string ".cctor"</span></span>|
|<span data-ttu-id="b1f2d-146">Yok edici</span><span class="sxs-lookup"><span data-stu-id="b1f2d-146">Destructor</span></span>|<span data-ttu-id="b1f2d-147">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="b1f2d-147">The string "Finalize"</span></span>|
|<span data-ttu-id="b1f2d-148">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b1f2d-148">User-defined operators or conversions</span></span>|<span data-ttu-id="b1f2d-149">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="b1f2d-150">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="b1f2d-150">Attribute constructor</span></span>|<span data-ttu-id="b1f2d-151">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="b1f2d-152">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="b1f2d-153">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="b1f2d-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="b1f2d-154">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b1f2d-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-155">See also</span></span>
 [<span data-ttu-id="b1f2d-156">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1f2d-156">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="b1f2d-157">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b1f2d-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="b1f2d-158">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="b1f2d-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
