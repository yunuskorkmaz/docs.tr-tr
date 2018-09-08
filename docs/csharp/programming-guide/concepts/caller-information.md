---
title: Arayan bilgileri (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 048e91ad337f74ef04a2a03412a44a0be0ef9506
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131331"
---
# <a name="caller-information-c"></a><span data-ttu-id="8c7cb-102">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7cb-102">Caller Information (C#)</span></span>
<span data-ttu-id="8c7cb-103">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="8c7cb-104">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="8c7cb-105">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="8c7cb-106">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="8c7cb-107">Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="8c7cb-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="8c7cb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8c7cb-108">Attribute</span></span>|<span data-ttu-id="8c7cb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c7cb-109">Description</span></span>|<span data-ttu-id="8c7cb-110">Tür</span><span class="sxs-lookup"><span data-stu-id="8c7cb-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="8c7cb-111">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="8c7cb-112">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="8c7cb-113">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="8c7cb-114">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-114">Method or property name of the caller.</span></span> <span data-ttu-id="8c7cb-115">Bkz: [üye adları](#MEMBERNAMES) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="8c7cb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c7cb-116">Example</span></span>  
 <span data-ttu-id="8c7cb-117">Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="8c7cb-118">Her çağrıda `TraceMessage` yöntemi arayan bilgileri isteğe bağlı parametrelerin bağımsız değişkenleri olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
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
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a><span data-ttu-id="8c7cb-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c7cb-119">Remarks</span></span>  
 <span data-ttu-id="8c7cb-120">Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="8c7cb-121">İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="8c7cb-122">Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="8c7cb-123">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="8c7cb-124">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="8c7cb-125">Tersine sonuçlar <xref:System.Exception.StackTrace%2A> özelliği için özel durumlar, sonuçlar gizlemeden etkilenmez etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="8c7cb-126">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <a name="MEMBERNAMES"></a> <span data-ttu-id="8c7cb-127">Üye adları</span><span class="sxs-lookup"><span data-stu-id="8c7cb-127">Member Names</span></span>  
 <span data-ttu-id="8c7cb-128">Kullanabileceğiniz `CallerMemberName` üye adı olarak belirtmekten kaçınmak için öznitelik bir `String` çağrılan yöntemin bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="8c7cb-129">Bu tekniği kullanarak, sorundan kaçınmak, **düzenlemeyi yeniden adlandırma** değişmez `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="8c7cb-130">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="8c7cb-130">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="8c7cb-131">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-131">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="8c7cb-132">Uygulama <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama sırasında arabirim.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="8c7cb-133">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="8c7cb-134">Olmadan `CallerMemberName` öznitelik, özellik adını değişmez değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="8c7cb-135">Aşağıdaki grafik üyesi kullandığınızda döndürülen adlarını gösterir. `CallerMemberName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="8c7cb-136">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="8c7cb-136">Calls occurs within</span></span>|<span data-ttu-id="8c7cb-137">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="8c7cb-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="8c7cb-138">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="8c7cb-138">Method, property, or event</span></span>|<span data-ttu-id="8c7cb-139">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="8c7cb-140">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="8c7cb-140">Constructor</span></span>|<span data-ttu-id="8c7cb-141">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="8c7cb-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="8c7cb-142">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="8c7cb-142">Static constructor</span></span>|<span data-ttu-id="8c7cb-143">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="8c7cb-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="8c7cb-144">Yok edici</span><span class="sxs-lookup"><span data-stu-id="8c7cb-144">Destructor</span></span>|<span data-ttu-id="8c7cb-145">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="8c7cb-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="8c7cb-146">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="8c7cb-146">User-defined operators or conversions</span></span>|<span data-ttu-id="8c7cb-147">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="8c7cb-148">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="8c7cb-148">Attribute constructor</span></span>|<span data-ttu-id="8c7cb-149">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="8c7cb-150">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="8c7cb-151">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="8c7cb-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="8c7cb-152">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c7cb-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c7cb-153">See Also</span></span>

- [<span data-ttu-id="8c7cb-154">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7cb-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="8c7cb-155">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7cb-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
- [<span data-ttu-id="8c7cb-156">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="8c7cb-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [<span data-ttu-id="8c7cb-157">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7cb-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
