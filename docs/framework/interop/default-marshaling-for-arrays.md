---
title: Diziler için Varsayılan Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181458"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="a9796-102">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="a9796-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="a9796-103">Tamamen yönetilen koddan oluşan bir uygulamada, ortak dil çalışma süresi dizi türlerini Giriş/Çıkış parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="a9796-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="a9796-104">Buna karşılık, interop mareşal varsayılan olarak parametrelerolarak bir dizi geçer.</span><span class="sxs-lookup"><span data-stu-id="a9796-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="a9796-105">[Sabitleme optimizasyonu](copying-and-pinning.md)ile, aynı dairedeki nesnelerle etkileşimde bulunan bir blittable dizi, In/Out parametresi olarak çalışıyor gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="a9796-106">Ancak, daha sonra kodu makineler arası proxy oluşturmak için kullanılan bir tür kitaplığına dışa aktarırsanız ve bu kitaplık çağrılarınızı daireler arasında mareşallik etmek için kullanılırsa, aramalar parametre davranışında doğru ya da doğru ya da gerçek olarak geri döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="a9796-107">Diziler doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki ayrımlar diğer blittable olmayan türlere göre daha fazla bilgi garanti eder.</span><span class="sxs-lookup"><span data-stu-id="a9796-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="a9796-108">Yönetilen Diziler</span><span class="sxs-lookup"><span data-stu-id="a9796-108">Managed Arrays</span></span>  
 <span data-ttu-id="a9796-109">Yönetilen dizi türleri değişebilir; ancak, <xref:System.Array?displayProperty=nameWithType> sınıf tüm dizi türlerinin taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="a9796-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="a9796-110">**System.Array** sınıfı, bir dizinin derecesini, uzunluğunu ve alt ve üst sınırlarını belirleyen özelliklerin yanı sıra dizilere erişme, sıralama, arama, kopyalama ve oluşturma yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a9796-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="a9796-111">Bu dizi türleri dinamiktir ve taban sınıf kitaplığında tanımlanan karşılık gelen statik türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="a9796-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="a9796-112">Bu dizi farklı bir tür olarak öğe türü ve sıralama her kombinasyonu düşünmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="a9796-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="a9796-113">Bu nedenle, tek boyutlu bir tamsayı dizisi, çift tiplerden oluşan tek boyutlu bir diziden farklı bir türdedir.</span><span class="sxs-lookup"><span data-stu-id="a9796-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="a9796-114">Benzer şekilde, iki boyutlu bir tamsayı dizisi, tek boyutlu bir tamsayı dizisinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a9796-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="a9796-115">Türleri karşılaştırırken dizinin sınırları dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="a9796-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="a9796-116">Aşağıdaki tabloda görüldüğü gibi, yönetilen dizinin herhangi bir örneğinin belirli bir öğe türü, rütbe ve alt sınır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9796-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="a9796-117">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="a9796-117">Managed array type</span></span>|<span data-ttu-id="a9796-118">Eleman türü</span><span class="sxs-lookup"><span data-stu-id="a9796-118">Element type</span></span>|<span data-ttu-id="a9796-119">Derece</span><span class="sxs-lookup"><span data-stu-id="a9796-119">Rank</span></span>|<span data-ttu-id="a9796-120">Alt sınır</span><span class="sxs-lookup"><span data-stu-id="a9796-120">Lower bound</span></span>|<span data-ttu-id="a9796-121">İmza gösterimi</span><span class="sxs-lookup"><span data-stu-id="a9796-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="a9796-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a9796-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="a9796-123">Türüne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-123">Specified by type.</span></span>|<span data-ttu-id="a9796-124">Rütbeye göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-124">Specified by rank.</span></span>|<span data-ttu-id="a9796-125">İsteğe bağlı olarak sınırlara göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="a9796-126">*yazın* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="a9796-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="a9796-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="a9796-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="a9796-128">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="a9796-128">Unknown</span></span>|<span data-ttu-id="a9796-129">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="a9796-129">Unknown</span></span>|<span data-ttu-id="a9796-130">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="a9796-130">Unknown</span></span>|<span data-ttu-id="a9796-131">**Array**</span><span class="sxs-lookup"><span data-stu-id="a9796-131">**System.Array**</span></span>|  
|<span data-ttu-id="a9796-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="a9796-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="a9796-133">Türüne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-133">Specified by type.</span></span>|<span data-ttu-id="a9796-134">1</span><span class="sxs-lookup"><span data-stu-id="a9796-134">1</span></span>|<span data-ttu-id="a9796-135">0</span><span class="sxs-lookup"><span data-stu-id="a9796-135">0</span></span>|<span data-ttu-id="a9796-136">*yazın* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="a9796-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="a9796-137">Yönetilmeyen Diziler</span><span class="sxs-lookup"><span data-stu-id="a9796-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="a9796-138">Yönetilmeyen diziler, COM tarzı güvenli diziler veya sabit veya değişken uzunlukta C tarzı dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="a9796-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="a9796-139">Güvenli diziler, ilişkili dizi verilerinin türünü, sıralamasını ve sınırlarını taşıyan kendi kendini açıklayan dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="a9796-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="a9796-140">C stili diziler, sabit alt sınırı 0 olan tek boyutlu daktisol dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="a9796-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="a9796-141">Mareşallik hizmeti, her iki dizi türü için de sınırlı bir desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a9796-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="a9796-142">Dizi Parametrelerinin .NET Koduna Geçirilmesi</span><span class="sxs-lookup"><span data-stu-id="a9796-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="a9796-143">Hem C stili diziler hem de güvenli diziler ,güvenli bir dizi veya C stili dizi olarak yönetilmeyen koddan .NET koduna geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="a9796-144">Aşağıdaki tabloyönetilmeyen türü değerini ve alınan türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9796-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="a9796-145">Yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="a9796-145">Unmanaged type</span></span>|<span data-ttu-id="a9796-146">Alınan tür</span><span class="sxs-lookup"><span data-stu-id="a9796-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="a9796-147">**SafeArray (** *Türü* **)**</span><span class="sxs-lookup"><span data-stu-id="a9796-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="a9796-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="a9796-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="a9796-149">Sıralama = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="a9796-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="a9796-150">Boyut yalnızca yönetilen imzada sağlanırsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9796-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="a9796-151">Rank = 1 veya alt bound = 0 olmayan güvenli diziler **SZARRAY**olarak marshaled olamaz.</span><span class="sxs-lookup"><span data-stu-id="a9796-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="a9796-152">*Türü*  **[]**</span><span class="sxs-lookup"><span data-stu-id="a9796-152">*Type*  **[]**</span></span>|<span data-ttu-id="a9796-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="a9796-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="a9796-154">Sıralama = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="a9796-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="a9796-155">Boyut yalnızca yönetilen imzada sağlanırsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9796-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="a9796-156">Güvenli Diziler</span><span class="sxs-lookup"><span data-stu-id="a9796-156">Safe Arrays</span></span>  
 <span data-ttu-id="a9796-157">Güvenli bir dizi bir tür kitaplığından bir .NET derlemesine aktarıldığında, dizi bilinen bir türün tek boyutlu dizisine **(int**gibi) dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9796-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="a9796-158">Parametreler için geçerli olan aynı tür dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9796-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="a9796-159">Örneğin, güvenli bir **BSTR** türü dizisi yönetilen bir dize dizisi ne de güvenli bir türdizi yönetilen bir nesne dizisi olur.</span><span class="sxs-lookup"><span data-stu-id="a9796-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="a9796-160">**SAFEARRAY** öğe türü tür kitaplığından yakalanır ve numaralandırmanın <xref:System.Runtime.InteropServices.UnmanagedType> **SAFEARRAY** değerine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="a9796-161">Güvenli dizinin sıralaması ve sınırları tür kitaplığından belirlenemediğinden, sıralama 1'e eşit, alt sınır ise 0'a eşit olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="a9796-162">Sıralama ve [sınırlar, Tip Kitaplığı İthalatçısı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından üretilen yönetilen imzada tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9796-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="a9796-163">Çalışma zamanında yönteme geçirilen sıralama farklıysa, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> bir atılır.</span><span class="sxs-lookup"><span data-stu-id="a9796-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="a9796-164">Çalışma zamanında geçirilen dizi türü farklıysa, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> bir atılır.</span><span class="sxs-lookup"><span data-stu-id="a9796-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="a9796-165">Aşağıdaki örnek, yönetilen ve yönetilmeyen koddaki güvenli dizileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9796-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="a9796-166">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-166">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="a9796-167">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-167">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 <span data-ttu-id="a9796-168">Tlbimp.exe tarafından üretilen yöntem imzası **ELEMENT_TYPE_SZARRAY**yerine **bir ELEMENT_TYPE_ARRAY** öğe türünü belirtmek üzere değiştirilirse, çok boyutlu veya sıfıra bağlı olmayan güvenli diziler yönetilen koda dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="a9796-169">Alternatif olarak, tüm dizileri nesne olarak <xref:System.Array?displayProperty=nameWithType> almak için Tlbimp.exe ile **/sysarray** anahtarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9796-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="a9796-170">Geçirilen dizinin çok boyutlu olduğu bilinen durumlarda, Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyebilir ve yeniden derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9796-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="a9796-171">MSIL kodunu niçin değiştireceğimiz hakkında ayrıntılı bilgi için [Runtime Çağrılı Paketleyicilerini Özelleştirme'ye](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="a9796-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="a9796-172">C-Style Diziler</span><span class="sxs-lookup"><span data-stu-id="a9796-172">C-Style Arrays</span></span>  
 <span data-ttu-id="a9796-173">C stili bir dizi bir tür kitaplığından .NET derlemesine aktarıldığında, dizi **ELEMENT_TYPE_SZARRAY**dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9796-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="a9796-174">Dizi öğesi türü tür kitaplığından belirlenir ve alma sırasında korunur.</span><span class="sxs-lookup"><span data-stu-id="a9796-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="a9796-175">Parametreler için geçerli olan aynı dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9796-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="a9796-176">Örneğin, bir dizi **LPD** türü String **türleri** dizisi olur.</span><span class="sxs-lookup"><span data-stu-id="a9796-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="a9796-177">Tlbimp.exe dizi öğesi türünü yakalar ve <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametreöze özniteliği uygular.</span><span class="sxs-lookup"><span data-stu-id="a9796-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="a9796-178">Dizi sıralaması 1'e eşit olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="a9796-179">Sıralama 1'den büyükse, dizi sütun-ana sırada tek boyutlu bir dizi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="a9796-180">Alt sınır her zaman 0'a eşittir.</span><span class="sxs-lookup"><span data-stu-id="a9796-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="a9796-181">Tür kitaplıkları sabit veya değişken uzunlukta diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="a9796-182">Tür kitaplıkları değişken uzunluktaki dizileri mareşallemek için gereken bilgilerden yoksun olduğundan, Tlbimp.exe tür kitaplıklarından yalnızca sabit uzunlukta diziler içe aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="a9796-183">Sabit uzunluktadizilerle boyut, tür kitaplığından alınır ve parametreye uygulanan **MarshalAsÖz'de** yakalanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="a9796-184">Aşağıdaki örnekte gösterildiği gibi, değişken uzunlukta diziler içeren tür kitaplıklarını el ile tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9796-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="a9796-185">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-185">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="a9796-186">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-186">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="a9796-187">**Boyutu** istemciye iletmek için Size_is veya **length_is** özniteliklerini Arabirim Tanımı Dili (IDL) kaynağındaki bir diziye uygulayabilirsiniz, ancak Microsoft Arabirim Tanım Dili (MIDL) derleyicisi bu bilgileri tür kitaplığına yaymaz.</span><span class="sxs-lookup"><span data-stu-id="a9796-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="a9796-188">Boyutunu bilmeden, interop mareşallik hizmeti dizi öğelerini karemleyemez.</span><span class="sxs-lookup"><span data-stu-id="a9796-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="a9796-189">Sonuç olarak, değişken uzunluktaki diziler başvuru bağımsız değişkenleri olarak içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="a9796-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="a9796-190">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-190">For example:</span></span>  
  
 <span data-ttu-id="a9796-191">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-191">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="a9796-192">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="a9796-192">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 <span data-ttu-id="a9796-193">Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyip yeniden derleyerek mareşale dizi boyutunu sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9796-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="a9796-194">MSIL kodunu niçin değiştireceğimiz hakkında ayrıntılı bilgi için [Runtime Çağrılı Paketleyicilerini Özelleştirme'ye](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="a9796-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="a9796-195">Dizideki öğe sayısını belirtmek için, <xref:System.Runtime.InteropServices.MarshalAsAttribute> türü yönetilen yöntem tanımının dizi parametresine aşağıdaki yollardan biriyle uygulayın:</span><span class="sxs-lookup"><span data-stu-id="a9796-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="a9796-196">Dizideki öğe sayısını içeren başka bir parametre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a9796-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="a9796-197">Parametreler, ilk parametre den başlayarak 0 sayısı olarak konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a9796-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="a9796-198">Dizinin boyutunu sabit olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a9796-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="a9796-199">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="a9796-200">Dizileri yönetilmeyen koddan yönetilen koda göre sıralarken, mareşal dizi boyutunu belirlemek için parametreyle ilişkili **MarshalAsÖzniteliğini** denetler.</span><span class="sxs-lookup"><span data-stu-id="a9796-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="a9796-201">Dizi boyutu belirtilmemişse, yalnızca bir öğe marshaled.</span><span class="sxs-lookup"><span data-stu-id="a9796-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9796-202">**MarshalAsAttribute** yönetilen dizileri yönetilmeyen kodiçin mareşal üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a9796-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="a9796-203">Bu doğrultuda, dizi boyutu inceleyerek belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a9796-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="a9796-204">Yönetilen bir dizinin bir alt kümesini mareşallemek için bir yol yoktur.</span><span class="sxs-lookup"><span data-stu-id="a9796-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="a9796-205">Interop marshaler ayırmak ve bellek almak için **CoTaskMemAlloc** ve **CoTaskMemFree** yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="a9796-206">Yönetilmeyen kod tarafından gerçekleştirilen bellek ayırma da bu yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9796-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="a9796-207">Dizileri COM'a Geçirme</span><span class="sxs-lookup"><span data-stu-id="a9796-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="a9796-208">Yönetilen tüm dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="a9796-209">Yönetilen türe ve uygulanan özniteliklere bağlı olarak, diziaşağıdaki tabloda gösterildiği gibi güvenli bir dizi veya C stili dizi olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a9796-210">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="a9796-210">Managed array type</span></span>|<span data-ttu-id="a9796-211">Dışa aktarılan</span><span class="sxs-lookup"><span data-stu-id="a9796-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="a9796-212">**ELEMENT_TYPE_SZARRAY** **\<** *türü\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="a9796-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="a9796-213"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *türü)* **)**</span><span class="sxs-lookup"><span data-stu-id="a9796-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a9796-214">**YönetilmeyenType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="a9796-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="a9796-215">Yazı imzada sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-215">Type is provided in the signature.</span></span> <span data-ttu-id="a9796-216">Rütbe her zaman 1, alt sınır her zaman 0'dır.</span><span class="sxs-lookup"><span data-stu-id="a9796-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="a9796-217">Boyut her zaman çalışma zamanında bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9796-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="a9796-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** türü**\<** *sıralama* *bounds* **>**[ sınırlar ] **>**</span><span class="sxs-lookup"><span data-stu-id="a9796-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="a9796-219">**YönetilmeyenType.SafeArray(** *türü)* **)**</span><span class="sxs-lookup"><span data-stu-id="a9796-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a9796-220">**YönetilmeyenType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="a9796-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="a9796-221">Yazı, rütbe, sınırlar imzada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a9796-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="a9796-222">Boyut her zaman çalışma zamanında bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9796-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="a9796-223">**ELEMENT_TYPE_CLASS\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="a9796-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="a9796-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="a9796-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="a9796-225">**YönetilmeyenType.SafeArray(** *türü)* **)**</span><span class="sxs-lookup"><span data-stu-id="a9796-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a9796-226">Türü, sıralaması, sınırları ve boyutu her zaman çalışma zamanında bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9796-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="a9796-227">OLE Otomasyonu'nda LPSTR veya LPWSTR içeren yapı dizileri ile ilgili bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="a9796-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="a9796-228">Bu nedenle, **String** alanları **UnmanagedType.BSTR**olarak marshaled olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9796-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="a9796-229">Aksi takdirde, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="a9796-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="a9796-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="a9796-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="a9796-231">**ELEMENT_TYPE_SZARRAY** parametresi (tek boyutlu dizi) içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY'ine** dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9796-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="a9796-232">Aynı dönüştürme kuralları dizi öğesi türleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9796-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="a9796-233">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY'e**otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="a9796-234">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-235">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a9796-236">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-236">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="a9796-237">Güvenli dizilerin sıralaması her zaman 1 ve alt sınır her zaman 0'dır.</span><span class="sxs-lookup"><span data-stu-id="a9796-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="a9796-238">Boyut, geçirilen yönetilen dizinin boyutuna göre çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a9796-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="a9796-239">Dizi, öznitelik kullanılarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> C stili dizi olarak da düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a9796-240">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-241">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-241">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a9796-242">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-242">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="a9796-243">Mareşal, diziyi mareşallemek için gereken uzunluk bilgilerine sahip olsa da, dizi uzunluğu genellikle uzunluğu callee'ye iletmek için ayrı bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="a9796-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="a9796-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="a9796-245">**bir ELEMENT_TYPE_ARRAY** parametresi içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY'ine** dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9796-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="a9796-246">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY'e**otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a9796-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="a9796-247">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-248">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a9796-249">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-249">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="a9796-250">Güvenli dizilerin sıralaması, boyutu ve sınırları, yönetilen dizinin özelliklerine göre çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a9796-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="a9796-251">Dizi, öznitelik uygulanarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> C stili dizi olarak da marshaled olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a9796-252">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-253">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-253">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a9796-254">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-254">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="a9796-255">İç içe diziler marshaled olamaz.</span><span class="sxs-lookup"><span data-stu-id="a9796-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="a9796-256">Örneğin, Tür [Kitaplığı İhracatçısı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışa aktarıldığında aşağıdaki imza bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9796-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-257">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="a9796-258">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="a9796-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="a9796-259"><xref:System.Array?displayProperty=nameWithType> Parametre içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi **_Array** arabirimine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a9796-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="a9796-260">Yönetilen dizinin içeriğine yalnızca **_Array** arabiriminin yöntemleri ve özellikleri yle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="a9796-261">**System.Array** özniteliği kullanılarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> **safearray** olarak da marshaled olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a9796-262">Güvenli bir dizi olarak marshaled zaman, dizi öğeleri varyantları olarak marshaled.</span><span class="sxs-lookup"><span data-stu-id="a9796-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="a9796-263">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a9796-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a9796-264">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a9796-265">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="a9796-265">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="a9796-266">Yapılar içindeki diziler</span><span class="sxs-lookup"><span data-stu-id="a9796-266">Arrays within Structures</span></span>  
 <span data-ttu-id="a9796-267">Yönetilmeyen yapılar katıştırılmış diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="a9796-268">Varsayılan olarak, bu katıştılı dizi alanları SAFEARRAY olarak marshaled.</span><span class="sxs-lookup"><span data-stu-id="a9796-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="a9796-269">Aşağıdaki örnekte, `s1` doğrudan yapının kendi içinde ayrılmış gömülü bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="a9796-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="a9796-270">Yönetilmeyen gösterim</span><span class="sxs-lookup"><span data-stu-id="a9796-270">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="a9796-271">Diziler, <xref:System.Runtime.InteropServices.UnmanagedType> <xref:System.Runtime.InteropServices.MarshalAsAttribute> alanı ayarlamanızı gerektiren bir dizi olarak düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="a9796-272">Boyutu yalnızca sabit olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a9796-272">The size can be set only as a constant.</span></span> <span data-ttu-id="a9796-273">Aşağıdaki kod, 'nin ilgili `MyStruct`yönetilen tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9796-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9796-274">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9796-274">See also</span></span>

- [<span data-ttu-id="a9796-275">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="a9796-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="a9796-276">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="a9796-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="a9796-277">[Yön Özellikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9796-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="a9796-278">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="a9796-278">Copying and Pinning</span></span>](copying-and-pinning.md)
