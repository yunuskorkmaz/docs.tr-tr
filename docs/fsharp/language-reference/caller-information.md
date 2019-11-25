---
title: Arayan bilgileri
description: Bir yöntemden çağıran bilgileri elde etmek için çağıran bilgileri bağımsız değişken özniteliklerinin nasıl kullanılacağını açıklar.
ms.date: 11/04/2019
ms.openlocfilehash: d995b37149277b7c7d1b6217ee484d3c90a7f8b3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976806"
---
# <a name="caller-information"></a><span data-ttu-id="43455-103">Arayan bilgileri</span><span class="sxs-lookup"><span data-stu-id="43455-103">Caller information</span></span>

<span data-ttu-id="43455-104">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43455-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="43455-105">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43455-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="43455-106">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="43455-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="43455-107">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43455-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="43455-108">Aşağıdaki tabloda, [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="43455-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="43455-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43455-109">Attribute</span></span>|<span data-ttu-id="43455-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43455-110">Description</span></span>|<span data-ttu-id="43455-111">Tür</span><span class="sxs-lookup"><span data-stu-id="43455-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="43455-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="43455-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="43455-113">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="43455-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="43455-114">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="43455-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="43455-115">Callerlinumarası</span><span class="sxs-lookup"><span data-stu-id="43455-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="43455-116">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="43455-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="43455-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="43455-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="43455-118">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="43455-118">Method or property name of the caller.</span></span> <span data-ttu-id="43455-119">Bu konunun ilerleyen kısımlarında bulunan üye adları bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="43455-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="43455-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="43455-120">Example</span></span>

<span data-ttu-id="43455-121">Aşağıdaki örnek, bir çağrıyı izlemek için bu öznitelikleri nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="43455-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a><span data-ttu-id="43455-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43455-122">Remarks</span></span>

<span data-ttu-id="43455-123">Çağıran bilgi öznitelikleri yalnızca isteğe bağlı parametrelere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="43455-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="43455-124">Çağıran bilgi öznitelikleri, derleyicinin bir arayan bilgileri özniteliğiyle donatılmış her bir isteğe bağlı parametre için uygun değeri yazmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="43455-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="43455-125">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="43455-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="43455-126">Özel durumlar için [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özelliğinin sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="43455-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="43455-127">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43455-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="43455-128">Üye adları</span><span class="sxs-lookup"><span data-stu-id="43455-128">Member names</span></span>

<span data-ttu-id="43455-129">Üyenin adını çağrılan metoda bir `String` bağımsız değişkeni olarak belirtmekten kaçınmak için [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43455-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="43455-130">Bu tekniği kullanarak, yeniden düzenlemeyi yeniden adlandırma sorununun `String` değerleri değiştirmediğini önleyin.</span><span class="sxs-lookup"><span data-stu-id="43455-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="43455-131">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="43455-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="43455-132">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="43455-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="43455-133">Verileri bağlarken [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) arabirimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="43455-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="43455-134">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="43455-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="43455-135">[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliği olmadan, özellik adını bir sabit değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="43455-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="43455-136">Aşağıdaki grafikte, CallerMemberName özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="43455-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="43455-137">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="43455-137">Calls occurs within</span></span>|<span data-ttu-id="43455-138">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="43455-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="43455-139">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="43455-139">Method, property, or event</span></span>|<span data-ttu-id="43455-140">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="43455-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="43455-141">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="43455-141">Constructor</span></span>|<span data-ttu-id="43455-142">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="43455-142">The string ".ctor"</span></span>|
|<span data-ttu-id="43455-143">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="43455-143">Static constructor</span></span>|<span data-ttu-id="43455-144">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="43455-144">The string ".cctor"</span></span>|
|<span data-ttu-id="43455-145">Yok edici</span><span class="sxs-lookup"><span data-stu-id="43455-145">Destructor</span></span>|<span data-ttu-id="43455-146">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="43455-146">The string "Finalize"</span></span>|
|<span data-ttu-id="43455-147">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="43455-147">User-defined operators or conversions</span></span>|<span data-ttu-id="43455-148">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="43455-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="43455-149">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="43455-149">Attribute constructor</span></span>|<span data-ttu-id="43455-150">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="43455-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="43455-151">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="43455-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="43455-152">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="43455-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="43455-153">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="43455-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="43455-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43455-154">See also</span></span>

- [<span data-ttu-id="43455-155">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43455-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="43455-156">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="43455-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="43455-157">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="43455-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
