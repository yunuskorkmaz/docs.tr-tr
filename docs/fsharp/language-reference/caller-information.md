---
title: 'Arayan bilgileri (F #)'
description: "Arayan bilgileri bağımsız değişkeni öznitelikleri bir yöntemden arayan bilgileri almak için nasıl kullanılacağını açıklar."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a><span data-ttu-id="7f7d5-104">Arayan bilgileri</span><span class="sxs-lookup"><span data-stu-id="7f7d5-104">Caller information</span></span>

<span data-ttu-id="7f7d5-105">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-105">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="7f7d5-106">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-106">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="7f7d5-107">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-107">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="7f7d5-108">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-108">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="7f7d5-109">Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanı:</span><span class="sxs-lookup"><span data-stu-id="7f7d5-109">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="7f7d5-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7f7d5-110">Attribute</span></span>|<span data-ttu-id="7f7d5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f7d5-111">Description</span></span>|<span data-ttu-id="7f7d5-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7f7d5-112">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="7f7d5-113">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="7f7d5-113">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="7f7d5-114">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-114">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="7f7d5-115">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-115">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="7f7d5-116">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="7f7d5-116">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="7f7d5-117">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-117">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="7f7d5-118">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="7f7d5-118">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="7f7d5-119">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-119">Method or property name of the caller.</span></span> <span data-ttu-id="7f7d5-120">Bu konunun ilerleyen bölümlerinde üye adlarının bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-120">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="7f7d5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f7d5-121">Example</span></span>

<span data-ttu-id="7f7d5-122">Aşağıdaki örnek, çağıran izlemek için bu öznitelikler nasıl kullanabileceğinize gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-122">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="7f7d5-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f7d5-123">Remarks</span></span>

<span data-ttu-id="7f7d5-124">Arayan bilgileri öznitelikleri için isteğe bağlı parametreler yalnızca uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-124">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="7f7d5-125">Her bir isteğe bağlı parametre için açık bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-125">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="7f7d5-126">Arayan bilgileri öznitelikleri arayan bilgileri özniteliği ile donatılmış her isteğe bağlı bir parametre uygun değeri yazmak derleyici neden.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-126">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="7f7d5-127">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="7f7d5-128">Sonuçlarını aksine [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özellik için özel durumlar, sonuçları gizleme tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-128">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="7f7d5-129">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="7f7d5-130">Üye adlarının</span><span class="sxs-lookup"><span data-stu-id="7f7d5-130">Member names</span></span>

<span data-ttu-id="7f7d5-131">Kullanabileceğiniz [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliği üye adı olarak belirtmekten kaçının bir `String` çağrılan yöntemin bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-131">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="7f7d5-132">Bu yöntemi kullanarak, yeniden adlandırma yeniden düzenleme değişmez bir sorunu önlemenize `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-132">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="7f7d5-133">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="7f7d5-133">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="7f7d5-134">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-134">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="7f7d5-135">Uygulama [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) veri bağlama sırasında arabirim.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-135">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="7f7d5-136">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="7f7d5-137">Olmadan [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) öznitelik, bir hazır değer özellik adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-137">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="7f7d5-138">Aşağıdaki grafikte üye CallerMemberName özniteliğini kullandığınızda, döndürülen adlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-138">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="7f7d5-139">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="7f7d5-139">Calls occurs within</span></span>|<span data-ttu-id="7f7d5-140">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="7f7d5-140">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="7f7d5-141">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="7f7d5-141">Method, property, or event</span></span>|<span data-ttu-id="7f7d5-142">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-142">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="7f7d5-143">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="7f7d5-143">Constructor</span></span>|<span data-ttu-id="7f7d5-144">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="7f7d5-144">The string ".ctor"</span></span>|
|<span data-ttu-id="7f7d5-145">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="7f7d5-145">Static constructor</span></span>|<span data-ttu-id="7f7d5-146">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="7f7d5-146">The string ".cctor"</span></span>|
|<span data-ttu-id="7f7d5-147">Yok edici</span><span class="sxs-lookup"><span data-stu-id="7f7d5-147">Destructor</span></span>|<span data-ttu-id="7f7d5-148">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="7f7d5-148">The string "Finalize"</span></span>|
|<span data-ttu-id="7f7d5-149">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="7f7d5-149">User-defined operators or conversions</span></span>|<span data-ttu-id="7f7d5-150">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-150">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="7f7d5-151">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="7f7d5-151">Attribute constructor</span></span>|<span data-ttu-id="7f7d5-152">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="7f7d5-153">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="7f7d5-154">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="7f7d5-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="7f7d5-155">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-155">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7f7d5-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f7d5-156">See also</span></span>
 [<span data-ttu-id="7f7d5-157">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="7f7d5-157">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="7f7d5-158">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7f7d5-158">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="7f7d5-159">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="7f7d5-159">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
