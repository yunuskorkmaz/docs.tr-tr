---
description: 'Daha fazla bilgi edinin: arayan bilgileri (Visual Basic)'
title: Arayan Bilgileri
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: bcb4f553a9840a76f24825c3c2b7e2e98914abc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437715"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="837d3-103">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="837d3-103">Caller Information (Visual Basic)</span></span>

<span data-ttu-id="837d3-104">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837d3-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="837d3-105">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837d3-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="837d3-106">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="837d3-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="837d3-107">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837d3-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="837d3-108">Aşağıdaki tabloda, ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="837d3-108">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="837d3-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="837d3-109">Attribute</span></span>|<span data-ttu-id="837d3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="837d3-110">Description</span></span>|<span data-ttu-id="837d3-111">Tür</span><span class="sxs-lookup"><span data-stu-id="837d3-111">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="837d3-112">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="837d3-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="837d3-113">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="837d3-113">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="837d3-114">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="837d3-114">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="837d3-115">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="837d3-115">Method or property name of the caller.</span></span> <span data-ttu-id="837d3-116">Bu konunun devamındaki [üye adları](#MEMBERNAMES) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="837d3-116">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="837d3-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="837d3-117">Example</span></span>  

 <span data-ttu-id="837d3-118">Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="837d3-118">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="837d3-119">Yöntemine yapılan her çağrıda `TraceMessage` , çağıran bilgileri isteğe bağlı parametrelere bağımsız değişkenler olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="837d3-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="837d3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="837d3-120">Remarks</span></span>  

 <span data-ttu-id="837d3-121">Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="837d3-121">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="837d3-122">İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="837d3-122">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="837d3-123">Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez.</span><span class="sxs-lookup"><span data-stu-id="837d3-123">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="837d3-124">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="837d3-124">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="837d3-125">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="837d3-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="837d3-126"><xref:System.Exception.StackTrace%2A>Özel durumlar için özellik sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="837d3-126">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="837d3-127">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837d3-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a> <span data-ttu-id="837d3-128">Üye adları</span><span class="sxs-lookup"><span data-stu-id="837d3-128">Member Names</span></span>  

 <span data-ttu-id="837d3-129">`CallerMemberName`Özniteliği, çağrılan yönteme bir bağımsız değişken olarak üye adını belirtmekten kaçınmak için kullanabilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="837d3-129">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="837d3-130">Bu tekniği kullanarak **yeniden düzenlemeyi yeniden adlandırma** sorunu, `String` değerleri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="837d3-130">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="837d3-131">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="837d3-131">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="837d3-132">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="837d3-132">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="837d3-133"><xref:System.ComponentModel.INotifyPropertyChanged>Verileri bağlarken arabirimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="837d3-133">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="837d3-134">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="837d3-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="837d3-135">Özniteliği olmadan `CallerMemberName` , özellik adını bir sabit değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="837d3-135">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="837d3-136">Aşağıdaki grafikte, özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir `CallerMemberName` .</span><span class="sxs-lookup"><span data-stu-id="837d3-136">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="837d3-137">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="837d3-137">Calls occurs within</span></span>|<span data-ttu-id="837d3-138">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="837d3-138">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="837d3-139">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="837d3-139">Method, property, or event</span></span>|<span data-ttu-id="837d3-140">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="837d3-140">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="837d3-141">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="837d3-141">Constructor</span></span>|<span data-ttu-id="837d3-142">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="837d3-142">The string ".ctor"</span></span>|  
|<span data-ttu-id="837d3-143">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="837d3-143">Static constructor</span></span>|<span data-ttu-id="837d3-144">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="837d3-144">The string ".cctor"</span></span>|  
|<span data-ttu-id="837d3-145">Yok edici</span><span class="sxs-lookup"><span data-stu-id="837d3-145">Destructor</span></span>|<span data-ttu-id="837d3-146">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="837d3-146">The string "Finalize"</span></span>|  
|<span data-ttu-id="837d3-147">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="837d3-147">User-defined operators or conversions</span></span>|<span data-ttu-id="837d3-148">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="837d3-148">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="837d3-149">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="837d3-149">Attribute constructor</span></span>|<span data-ttu-id="837d3-150">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="837d3-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="837d3-151">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="837d3-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="837d3-152">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="837d3-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="837d3-153">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="837d3-153">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="837d3-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="837d3-154">See also</span></span>

- [<span data-ttu-id="837d3-155">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="837d3-155">Attributes (Visual Basic)</span></span>](../../language-reference/attributes.md)
- [<span data-ttu-id="837d3-156">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="837d3-156">Common Attributes (Visual Basic)</span></span>](attributes/common-attributes.md)
- [<span data-ttu-id="837d3-157">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="837d3-157">Optional Parameters</span></span>](../language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="837d3-158">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="837d3-158">Programming Concepts (Visual Basic)</span></span>](index.md)
