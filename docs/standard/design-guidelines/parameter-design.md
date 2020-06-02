---
title: Parametre Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 46c1b8f03d054a63ea837a73fd30eeed163ab0a4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290103"
---
# <a name="parameter-design"></a><span data-ttu-id="9b645-102">Parametre tasarımı</span><span class="sxs-lookup"><span data-stu-id="9b645-102">Parameter design</span></span>

<span data-ttu-id="9b645-103">Bu bölüm, bağımsız değişkenleri denetlemeye yönelik yönergeleri içeren bölümler dahil olmak üzere parametre tasarımı hakkında kapsamlı yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="9b645-104">Ayrıca, [adlandırma parametrelerinde](naming-parameters.md)açıklanan yönergelere başvurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9b645-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="9b645-105">✔️, üyenin gerektirdiği işlevselliği sağlayan en az türetilmiş parametre türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b645-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="9b645-106">Örneğin, bir koleksiyonu tasarlandıran ve her öğeyi konsola yazdıran bir yöntem tasarlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="9b645-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="9b645-107">Bu tür bir yöntem, <xref:System.Collections.IEnumerable> veya değil parametre olarak ele <xref:System.Collections.ArrayList> alınmalıdır <xref:System.Collections.IList> .</span><span class="sxs-lookup"><span data-stu-id="9b645-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="9b645-108">❌Ayrılmış parametreleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="9b645-109">Daha sonraki bir sürümde bir üyeye daha fazla giriş gerekiyorsa, yeni bir aşırı yükleme eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="9b645-110">❌İşaretçi, işaretçi dizileri veya çok boyutlu diziler parametre olarak alan genel kullanıma açık yöntemlere sahip DEĞILDIR.</span><span class="sxs-lookup"><span data-stu-id="9b645-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="9b645-111">İşaretçiler ve çok boyutlu diziler düzgün şekilde kullanılması nispeten zordur.</span><span class="sxs-lookup"><span data-stu-id="9b645-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="9b645-112">Neredeyse tüm durumlarda, bu türleri parametre olarak almayı önlemek için API 'Ler yeniden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="9b645-113">✔️ `out` , tüm parametreleri ve `ref` parametreleri (parametre dizileri hariç), aşırı yüklemeler arasındaki parametre sıralaması içinde tutarsızlığa neden olsa bile tüm parametreleri (bkz. [üye aşırı yükleme](member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="9b645-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="9b645-114">`out`Parametreler ek dönüş değerleri olarak görülebilir ve bunları birlikte gruplandırmak yöntem imzasının daha kolay anlaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="9b645-115">✔️, Üyeler geçersiz kılınırken veya arabirim üyeleri uygularken adlandırma parametrelerinde tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="9b645-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="9b645-116">Bu, Yöntemler arasındaki ilişkiyi daha iyi bir şekilde iletir.</span><span class="sxs-lookup"><span data-stu-id="9b645-116">This better communicates the relationship between the methods.</span></span>

### <a name="choose-between-enum-and-boolean-parameters"></a><span data-ttu-id="9b645-117">Enum ve Boole parametreleri arasında seçim yapın</span><span class="sxs-lookup"><span data-stu-id="9b645-117">Choose between enum and boolean parameters</span></span>
 <span data-ttu-id="9b645-118">✔️, bir üyenin iki veya daha fazla Boole parametresine sahip olması halinde numaralandırmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b645-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="9b645-119">❌İki değerden daha fazla değere gerek olmadığından kesinlikle emin olmadığınız müddetçe, Boolean kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="9b645-120">Numaralandırmalar, daha sonra değerlerin eklenmesi için bir yer sağlar, ancak [enum tasarımında açıklanan numaralandırıcılara](enum.md)değer eklemenin tüm etkilerine dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b645-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="9b645-121">✔️, gerçekten iki durumlu değerler olan Oluşturucu parametreleri için Boolean kullanmayı düşünün ve yalnızca Boole özelliklerini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b645-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validate-arguments"></a><span data-ttu-id="9b645-122">Bağımsız değişkenleri doğrula</span><span class="sxs-lookup"><span data-stu-id="9b645-122">Validate arguments</span></span>
 <span data-ttu-id="9b645-123">✔️ ortak, korumalı veya açıkça uygulanmış üyelere geçirilen bağımsız değişkenleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="9b645-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="9b645-124"><xref:System.ArgumentException?displayProperty=nameWithType>Doğrulama başarısız olursa, veya alt sınıflarından biri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b645-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="9b645-125">Gerçek doğrulamanın ortak veya korumalı üyenin kendisinde olması gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="9b645-126">Bu, bazı özel veya iç bir yordamın daha düşük bir düzeyinde gerçekleşecektir.</span><span class="sxs-lookup"><span data-stu-id="9b645-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="9b645-127">Ana nokta, son kullanıcılara sunulan tüm yüzey alanının bağımsız değişkenleri denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="9b645-128"><xref:System.ArgumentNullException>null bir bağımsız değişken geçirilmezse ve üye null bağımsız değişkenleri desteklemiyorsa ✔️ throw.</span><span class="sxs-lookup"><span data-stu-id="9b645-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="9b645-129">Enum parametrelerini doğrulamak ✔️.</span><span class="sxs-lookup"><span data-stu-id="9b645-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="9b645-130">Enum bağımsız değişkenlerinin enum tarafından tanımlanan aralıkta olacağını varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="9b645-131">CLR, değer numaralandırmasında tanımlanmasa bile herhangi bir tamsayı değerini bir sabit listesi değerine dönüştürmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="9b645-132">❌<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>Enum Aralık denetimleri için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="9b645-133">✔️, kesilebilir bağımsız değişkenlerin doğrulandıktan sonra değişmiş olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="9b645-134">Üye güvenliğe duyarlı ise, bir kopya yapmanız ve sonra bağımsız değişkeni doğrulamanız ve işlemesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="pass-parameters"></a><span data-ttu-id="9b645-135">Parametre geçirme</span><span class="sxs-lookup"><span data-stu-id="9b645-135">Pass parameters</span></span>
 <span data-ttu-id="9b645-136">Bir çerçeve tasarımcısının perspektifinden, üç temel parametre grubu vardır: değere göre parametreler, `ref` Parametreler ve `out` Parametreler.</span><span class="sxs-lookup"><span data-stu-id="9b645-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="9b645-137">Bir bağımsız değişken bir by değeri parametresiyle geçirildiğinde, üye geçirilen gerçek bağımsız değişkenin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="9b645-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="9b645-138">Bağımsız değişken bir değer türü ise, bağımsız değişkenin bir kopyası yığına konur.</span><span class="sxs-lookup"><span data-stu-id="9b645-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="9b645-139">Bağımsız değişken bir başvuru türü ise, başvurunun bir kopyası yığına konur.</span><span class="sxs-lookup"><span data-stu-id="9b645-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="9b645-140">C#, Visual Basic ve C++ gibi en popüler CLR dilleri, parametreleri değere göre geçirmek için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="9b645-140">Most popular CLR languages, such as C#, Visual Basic, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="9b645-141">Bir bağımsız değişken bir parametre aracılığıyla geçirildiğinde `ref` , üye geçirilen gerçek bağımsız değişkene bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="9b645-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="9b645-142">Bağımsız değişken bir değer türü ise, yığına bağımsız değişkene bir başvuru konur.</span><span class="sxs-lookup"><span data-stu-id="9b645-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="9b645-143">Bağımsız değişken bir başvuru türü ise, bir başvuruya başvuru, yığına konur.</span><span class="sxs-lookup"><span data-stu-id="9b645-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="9b645-144">`Ref`Parametreler, üyenin çağıran tarafından geçirilen bağımsız değişkenleri değiştirmesine izin vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="9b645-145">`Out`parametreler `ref` , bazı küçük farklılıklar ile parametrelere benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9b645-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="9b645-146">Parametre başlangıçta atanmamış olarak kabul edilir ve bir değer atanmadan önce üye gövdesinde okunamaz.</span><span class="sxs-lookup"><span data-stu-id="9b645-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="9b645-147">Ayrıca, parametreye, üyenin döndürdüğü bir değere atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b645-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="9b645-148">❌`out`Veya parametreleri kullanmaktan kaçının `ref` .</span><span class="sxs-lookup"><span data-stu-id="9b645-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="9b645-149">`out`Veya `ref` parametrelerinin kullanılması, işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeriyle yöntemleri işleme.</span><span class="sxs-lookup"><span data-stu-id="9b645-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="9b645-150">Ayrıca, `out` ve parametreleri arasındaki fark `ref` yaygın olarak anlaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="9b645-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="9b645-151">Genel bir hedef kitle için tasarlayan çerçeve mimarları, kullanıcıların, veya parametreleriyle birlikte çalışmasını beklememelidir `out` `ref` .</span><span class="sxs-lookup"><span data-stu-id="9b645-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="9b645-152">❌Başvuru türlerini başvuruya göre geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="9b645-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="9b645-153">Kural için, başvuruları değiştirmek için kullanılabilecek bir yöntem gibi bazı sınırlı özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9b645-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="9b645-154">Değişken parametre sayısı olan Üyeler</span><span class="sxs-lookup"><span data-stu-id="9b645-154">Members with variable number of parameters</span></span>
 <span data-ttu-id="9b645-155">Değişken sayıda bağımsız değişken alan Üyeler, bir dizi parametresi sağlayarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="9b645-156">Örneğin, <xref:System.String> aşağıdaki yöntemi sağlar:</span><span class="sxs-lookup"><span data-stu-id="9b645-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="9b645-157">Bir Kullanıcı daha sonra <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi aşağıdaki şekilde çağırabilir:</span><span class="sxs-lookup"><span data-stu-id="9b645-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="9b645-158">C# params anahtar sözcüğünü bir dizi parametresine eklemek, parametreyi bir so adlı params dizi parametresine değiştirir ve geçici bir dizi oluşturmak için bir kısayol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="9b645-159">Bunu yapmak, kullanıcının dizi öğelerini doğrudan bağımsız değişken listesinde geçirerek yöntemi çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="9b645-160">Params anahtar sözcüğünün yalnızca parametre listesindeki son parametreye eklenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="9b645-161">Son kullanıcıların dizileri az sayıda öğe ile geçmesini bekleseniz, dizi parametrelerine params anahtar sözcüğünü eklemeyi düşünün ✔️.</span><span class="sxs-lookup"><span data-stu-id="9b645-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="9b645-162">Yaygın senaryolarda çok sayıda öğenin geçirilmesi bekleniyorsa, kullanıcılar muhtemelen bu öğeleri de satır içine geçirmeyecektir ve bu nedenle params anahtar sözcüğü gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9b645-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="9b645-163">❌Arayan girişi neredeyse her zaman bir dizide zaten olacaksa params dizilerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="9b645-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="9b645-164">Örneğin, bayt dizi parametrelerine sahip Üyeler tek tek baytlar ileterek neredeyse hiçbir şekilde çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="9b645-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="9b645-165">Bu nedenle, .NET Framework bayt dizi parametreleri params anahtar sözcüğünü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9b645-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="9b645-166">❌Dizi params dizi parametresini alan üye tarafından değiştirilirse params dizilerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="9b645-167">Birçok derleyicilerin bağımsız değişkenlerini çağrı sitesinde geçici bir diziye değiştirdiğinden, dizi geçici bir nesne olabilir ve bu nedenle dizideki tüm değişiklikler kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="9b645-168">daha karmaşık bir aşırı yükleme bunu kullanmasa bile, bir basit aşırı yüklemede params anahtar sözcüğünü kullanmayı düşünün ✔️.</span><span class="sxs-lookup"><span data-stu-id="9b645-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="9b645-169">Tüm aşırı yüklerde olmasa bile kullanıcılar bir aşırı yüklemede params dizisine sahip olacaksa kendinize sorun.</span><span class="sxs-lookup"><span data-stu-id="9b645-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>

 <span data-ttu-id="9b645-170">✔️ params anahtar sözcüğünü kullanmayı olanaklı kılmak için parametreleri sipariş etmek için deneyin.</span><span class="sxs-lookup"><span data-stu-id="9b645-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="9b645-171">✔️ Son derece performans duyarlı API 'lerde çok sayıda bağımsız değişkene sahip çağrılar için özel aşırı yüklemeler ve kod yolları sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9b645-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="9b645-172">Bu, API, az sayıda bağımsız değişkenle çağrıldığında dizi nesneleri oluşturmaktan kaçınılmasını mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="9b645-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="9b645-173">Parametre adlarını, dizi parametresinin tekil bir biçimini alarak ve sayısal bir sonek ekleyerek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b645-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="9b645-174">Bunu yalnızca bir dizi oluşturun ve daha genel yöntemi çağırmak için kod yolunun tamamına özel durum oluşturacaksanız yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b645-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="9b645-175">✔️, null bir params Array bağımsız değişkeni olarak geçirilebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="9b645-176">İşlemeden önce dizinin null olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b645-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="9b645-177">❌`varargs`Üç nokta olarak da bilinen yöntemleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b645-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="9b645-178">C++ gibi bazı CLR dilleri, yöntem olarak adlandırılan değişken parametre listelerinin geçirilmesi için alternatif bir kural destekler `varargs` .</span><span class="sxs-lookup"><span data-stu-id="9b645-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="9b645-179">Bu kural, CLS uyumlu olmadığından çerçeve içinde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b645-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="9b645-180">İşaretçi parametreleri</span><span class="sxs-lookup"><span data-stu-id="9b645-180">Pointer parameters</span></span>
 <span data-ttu-id="9b645-181">Genel olarak, işaretçiler iyi tasarlanmış bir yönetilen kod çerçevesinin genel yüzey alanında görünmemelidir.</span><span class="sxs-lookup"><span data-stu-id="9b645-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="9b645-182">Çoğu zaman işaretçiler kapsüllenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9b645-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="9b645-183">Ancak bazı durumlarda, birlikte çalışabilirlik nedenleriyle işaretçiler gereklidir ve bu gibi durumlarda işaretçiler kullanılması uygundur.</span><span class="sxs-lookup"><span data-stu-id="9b645-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="9b645-184">✔️, işaretçiler CLS uyumlu olmadığından, işaretçi bağımsız değişkeni alan tüm Üyeler için bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b645-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="9b645-185">❌İşaretçi bağımsız değişkenlerinin pahalı bağımsız değişken denetimini yapmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="9b645-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="9b645-186">✔️ işaretçileri olan üyeleri tasarlarken, işaretçiyle ilgili genel kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9b645-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="9b645-187">Örneğin, başlangıç dizinini geçirmeniz gerekmez, çünkü basit işaretçi aritmetiği aynı sonucu elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b645-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="9b645-188">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9b645-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9b645-189">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="9b645-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9b645-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b645-190">See also</span></span>

- [<span data-ttu-id="9b645-191">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9b645-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="9b645-192">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9b645-192">Framework Design Guidelines</span></span>](index.md)
