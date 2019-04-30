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
author: KrzysztofCwalina
ms.openlocfilehash: 5a0f6e0fab5d0f2fe8574e348fc6b8ae726eeb99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757410"
---
# <a name="parameter-design"></a><span data-ttu-id="877de-102">Parametre Tasarımı</span><span class="sxs-lookup"><span data-stu-id="877de-102">Parameter Design</span></span>
<span data-ttu-id="877de-103">Bu bölümde parametre tasarımı, bağımsız değişkenleri denetimini yönergeleri ile bölümler dahil olmak üzere geniş yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="877de-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="877de-104">Ayrıca, açıklanan yönergelere bakabilir [adlandırma parametreleri](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="877de-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="877de-105">**✓ DO** üyesi tarafından gerekli işlevselliği sağlayan en az türetilen parametre türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="877de-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="877de-106">Örneğin, bir koleksiyon numaralandırır ve her öğeyi konsola yazdırır bir yöntem tasarım istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="877de-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="877de-107">Bu tür bir yöntem zamanınızı <xref:System.Collections.IEnumerable> parametre olarak değil <xref:System.Collections.ArrayList> veya <xref:System.Collections.IList>, örneğin.</span><span class="sxs-lookup"><span data-stu-id="877de-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="877de-108">**X DO NOT** ayrılmış parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="877de-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="877de-109">Daha fazla üye girişe gelecekte yayımlanacak bir sürümde gerekirse, yeni aşırı eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="877de-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="877de-110">**X DO NOT** işaretçileri, işaretçileri dizileri ya da parametre olarak çok boyutlu diziler alırken yöntemleri genel olarak kullanıma.</span><span class="sxs-lookup"><span data-stu-id="877de-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="877de-111">İşaretçiler ve çok boyutlu diziler düzgün bir şekilde kullanmak oldukça zordur.</span><span class="sxs-lookup"><span data-stu-id="877de-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="877de-112">Bu tür parametreleri olarak almayı önlemek için hemen hemen tüm durumlarda, API'ler tasarlanması.</span><span class="sxs-lookup"><span data-stu-id="877de-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="877de-113">**✓ DO** tüm yerleştirin `out` tüm değeri tarafından aşağıdaki parametreleri ve `ref` parametreleri (hariç parametre dizileri) arasında aşırı sıralama parametresinde bir tutarsızlık sonuçlanır olsa bile (bkz [üyesi Aşırı yükleme](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="877de-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="877de-114">`out` Parametreleri fazladan dönüş değerleri olarak görülebilir ve Gruplama yoluyla yapar yöntem imzası daha kolay anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="877de-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="877de-115">**✓ DO** parametreleri üyeleri geçersiz kılarken adlandırma veya arabirim üyeleri uygulama tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="877de-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="877de-116">Bu yöntem arasındaki ilişkiyi daha iyi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="877de-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="877de-117">Enum ile Boole parametreleri arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="877de-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="877de-118">**✓ DO** üyesi aksi iki veya daha fazla Boolean parametreleri varsa numaralandırmaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="877de-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="877de-119">**X DO NOT** ayrıca ikiden fazla değerleri gereksinimini hiçbir zaman olacaktır kesinlikle emin olmadığınız sürece Boole değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="877de-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="877de-120">Numaralandırmalar gelecekteki ek değerler için yer sağlar, ancak anlatılan numaralandırmalar değerler ekleme tüm etkileri farkında olmalıdır [sabit listesi tasarımı](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="877de-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="877de-121">**✓ CONSIDER** gerçekten iki durumlu değerleri desteklenir ve yalnızca Boole özellikleri başlatmak için kullanılan Oluşturucu parametreleri Boole değerlerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="877de-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="877de-122">Bağımsız değişkenler doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="877de-122">Validating Arguments</span></span>  
 <span data-ttu-id="877de-123">**✓ DO** public, korumalı ya da açıkça gerçekleştirilen üyelerine geçirilen bağımsız değişken doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="877de-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="877de-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, veya doğrulama başarısız olursa alt sınıflarından biri.</span><span class="sxs-lookup"><span data-stu-id="877de-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="877de-125">Gerçek doğrulama ortak veya korumalı üye kendini olmasını zorunlu yok unutmayın.</span><span class="sxs-lookup"><span data-stu-id="877de-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="877de-126">Bazı özel veya iç yordamında daha düşük bir düzeyde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="877de-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="877de-127">Son kullanıcılara gösterilen yüzey alanının tamamını bağımsız değişkenler denetler ana noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="877de-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="877de-128">**✓ DO** throw <xref:System.ArgumentNullException> null bir bağımsız değişken geçirildi ve üye null bağımsız değişkenler desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="877de-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="877de-129">**✓ DO** enum parametreleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="877de-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="877de-130">Enum tarafından tanımlanan aralığın Enum bağımsız değişkenler olacak varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="877de-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="877de-131">CLR numaralandırma değeri tanımlanmamış olsa bile herhangi bir tamsayı değeri bir sabit listesi değeri atama sağlar.</span><span class="sxs-lookup"><span data-stu-id="877de-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="877de-132">**X DO NOT** kullanmak <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> enum aralığının denetler.</span><span class="sxs-lookup"><span data-stu-id="877de-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="877de-133">**✓ DO** bunlar doğrulanan sonra değişebilir bağımsız değişkenleri değişmiş olabilecek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="877de-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="877de-134">Güvenlik duyarlı üyesiyse bir kopyasını oluşturun ve ardından doğrulamak ve bağımsız değişken işlemek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="877de-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="877de-135">Parametre Geçirme</span><span class="sxs-lookup"><span data-stu-id="877de-135">Parameter Passing</span></span>  
 <span data-ttu-id="877de-136">Framework Tasarımcısı perspektifinden parametrelerinin üç ana grup vardır: değer tarafından parametreleri `ref` parametreleri ve `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="877de-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="877de-137">Bir bağımsız değişken değere göre parametresi aracılığıyla geçirilir, üye geçirilen gerçek bağımsız değişkenin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="877de-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="877de-138">Bağımsız değişken bir değer türü ise, bağımsız değişkenin bir kopyası yığına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="877de-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="877de-139">Bağımsız değişken bir başvuru türü ise yığında başvuru bir kopyasını konur.</span><span class="sxs-lookup"><span data-stu-id="877de-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="877de-140">Parametrelerin değere göre geçirme için C#, VB.NET ve C++, varsayılan gibi en popüler CLR diller.</span><span class="sxs-lookup"><span data-stu-id="877de-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="877de-141">Ne zaman bir bağımsız değişken geçirilir aracılığıyla bir `ref` parametresi, üye geçirilen gerçek bağımsız değişkenin bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="877de-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="877de-142">Bağımsız değişken bir değer türü ise, bir bağımsız değişkene başvuru yığına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="877de-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="877de-143">Bağımsız değişken bir başvuru türü ise yığında başvuru başvuru konur.</span><span class="sxs-lookup"><span data-stu-id="877de-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="877de-144">`Ref` Parametreler, üyeyi çağıran tarafından geçirilen bağımsız değişkenler değiştirmek izin vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="877de-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="877de-145">`Out` parametreleri benzer `ref` parametreleri, bazı küçük farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="877de-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="877de-146">Parametre başlangıçta kabul atanmamış ve bir değer atanmadan önce üye gövdesinde okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="877de-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="877de-147">Ayrıca, üye döndürmeden önce bazı değeri atanacak parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="877de-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="877de-148">**X AVOID** kullanarak `out` veya `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="877de-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="877de-149">Kullanarak `out` veya `ref` parametreleri deneyimi işaretçilerle değer türleri ve başvuru türleri farkı anlama ve işleme yöntemi ile birden çok değer gerektirir.</span><span class="sxs-lookup"><span data-stu-id="877de-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="877de-150">Ayrıca, arasındaki farkı `out` ve `ref` parametreleri anlaşılmadı.</span><span class="sxs-lookup"><span data-stu-id="877de-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="877de-151">Genel kitle için tasarlama framework mimarları asıl kullanıcılara değil beklediğiniz `out` veya `ref` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="877de-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="877de-152">**X DO NOT** başvuru türleri başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="877de-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="877de-153">Başvuruları takas etmek için kullanılan bir yöntem gibi kurala, sınırlı bazı özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="877de-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="877de-154">Değişken sayıda parametre ile üyeleri</span><span class="sxs-lookup"><span data-stu-id="877de-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="877de-155">Değişken sayıda bağımsız değişken alabilir üyeleri, bir dizi parametresi sağlayarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="877de-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="877de-156">Örneğin, <xref:System.String> aşağıdaki yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="877de-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="877de-157">Bir kullanıcı daha sonra çağırabilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemini aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="877de-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="877de-158">C# params anahtar sözcüğü bir dizi parametresine ekleme sözde params dizisi parametresi parametre değiştirir ve geçici bir dizin oluşturmak için bir kısayol sağlar.</span><span class="sxs-lookup"><span data-stu-id="877de-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="877de-159">Bunun yapılması, dizi öğeleri doğrudan bağımsız değişken listesinde geçirerek yöntemini çağırmak kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="877de-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="877de-160">Params anahtar sözcüğü parametre listesindeki son parametre için yalnızca eklenebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="877de-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="877de-161">**✓ CONSIDER** az sayıda öğesi dizilerle geçirmek için son kullanıcıların bekliyorsanız params anahtar sözcüğü dizi parametreleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="877de-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="877de-162">Beklenen sayıda ortak senaryolar geçirilir, kullanıcıların bu öğeleri satır içi yine de geçmez büyük olasılıkla ve böylece params anahtar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="877de-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="877de-163">**X AVOID** çağıran neredeyse her zaman giriş zaten bir dizide isterseniz params dizileri kullanma.</span><span class="sxs-lookup"><span data-stu-id="877de-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="877de-164">Örneğin, üyeleri Bayt dizisine parametreli neredeyse hiçbir zaman tek tek bayt geçirerek çağrılır.</span><span class="sxs-lookup"><span data-stu-id="877de-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="877de-165">Bu nedenle, .NET Framework'teki bayt dizisi parametreleri params anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="877de-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="877de-166">**X DO NOT** dizi params dizisi parametresi alma üyesi tarafından değiştirilirse params diziler kullanın.</span><span class="sxs-lookup"><span data-stu-id="877de-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="877de-167">Çoğu derleyici çağrı sitesini geçici bir diziye üye bağımsız değişkenleri dönüştürün olgu nedeniyle geçici bir nesne dizisi olabilir ve bu nedenle dizi yapılan tüm değişiklikler kaybolacak.</span><span class="sxs-lookup"><span data-stu-id="877de-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="877de-168">**✓ CONSIDER** daha karmaşık bir aşırı kullanılamadı olsa bile bir basit aşırı params anahtar sözcüğü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="877de-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="877de-169">Kendinize tüm aşırı yüklemeler olmasa bile params dizisi içinde aşırı yüklemelerden birine sahip kullanıcılar bildirmenizden durumunda sorun.</span><span class="sxs-lookup"><span data-stu-id="877de-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="877de-170">**✓ DO** params anahtar sözcüğü kullanmak mümkün kılmak için sipariş parametreleri deneyin.</span><span class="sxs-lookup"><span data-stu-id="877de-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="877de-171">**✓ CONSIDER** küçük sayıda bağımsız değişken son derece performans duyarlı API'lerde aramaları için özel aşırı ve kod yolları sağlama.</span><span class="sxs-lookup"><span data-stu-id="877de-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="877de-172">Bu API küçük sayıda bağımsız değişkenle çağrıldığında dizi nesnelerini oluşturmaktan kaçınmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="877de-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="877de-173">Tekil bir dizi parametrenin alma ve sayısal bir sonek ekleyerek parametrelerinin adları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="877de-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="877de-174">Özel durum için tüm kod yolu, yalnızca bir dizi oluşturun ve daha genel bir yöntemi çağırmak kullanacaksanız yalnızca bunu yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="877de-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="877de-175">**✓ DO** bu null params dizisi bağımsız değişken olarak geçirilen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="877de-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="877de-176">Dizi önce işleme null değil doğrulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="877de-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="877de-177">**X DO NOT** kullanmak `varargs` yöntemleri, aksi takdirde üç nokta bilinir.</span><span class="sxs-lookup"><span data-stu-id="877de-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="877de-178">Adlı değişken parametre listeleri geçirmek için alternatif bir kuralı C++ gibi bazı CLR dilleri destekleyen `varargs` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="877de-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="877de-179">CLS uyumlu olmadığından kurala çerçeveleri alanında kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="877de-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="877de-180">İşaretçi parametreleri</span><span class="sxs-lookup"><span data-stu-id="877de-180">Pointer Parameters</span></span>  
 <span data-ttu-id="877de-181">Genel olarak, işaretçiler, iyi tasarlanmış bir yönetilen kod framework'ün genel yüzey alanını görünmemelidir.</span><span class="sxs-lookup"><span data-stu-id="877de-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="877de-182">İşaretçileri, çoğu zaman, kapsüllenmiş.</span><span class="sxs-lookup"><span data-stu-id="877de-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="877de-183">Ancak, bazı durumlarda işaretçileri birlikte çalışabilirlik nedenlerle gereklidir ve bu gibi durumlarda işaretçileri kullanmak uygundur.</span><span class="sxs-lookup"><span data-stu-id="877de-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="877de-184">**✓ DO** işaretçileri CLS ile uyumlu olmadığı için bir işaretçi bağımsız değişken herhangi bir üyesi için bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="877de-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="877de-185">**X AVOID** pahalı bağımsız değişkeni işaretçi bağımsız denetimi yapılması.</span><span class="sxs-lookup"><span data-stu-id="877de-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="877de-186">**✓ DO** işaretçisi ile ilgili genel kurallar işaretçileri üyeleriyle tasarlarken izleyin.</span><span class="sxs-lookup"><span data-stu-id="877de-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="877de-187">Örneğin, basit bir işaretçi aritmetik aynı sonuca ulaşmak için kullanılabildiğinden başlangıç dizini geçirilecek gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="877de-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="877de-188">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="877de-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="877de-189">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="877de-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877de-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="877de-190">See also</span></span>

- [<span data-ttu-id="877de-191">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="877de-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="877de-192">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="877de-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
