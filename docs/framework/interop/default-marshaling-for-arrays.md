---
title: Diziler için Varsayılan Sıralama
description: Diziler için varsayılan hazırlamayı anlayın. Yönetilen dizileri, yönetilmeyen dizileri gözden geçirin, .NET koduna dizi parametreleri geçirme ve dizileri COM 'a geçirme.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: 6bfe95576a6460efac75fd392e24acf42e36f2de
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555269"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="c2665-104">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="c2665-104">Default Marshaling for Arrays</span></span>
<span data-ttu-id="c2665-105">Tamamen yönetilen koddan oluşan bir uygulamada, ortak dil çalışma zamanı dizi türlerini ın/out parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c2665-105">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="c2665-106">Buna karşılık, birlikte çalışma sıralayıcısı varsayılan olarak parametre olarak bir diziyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="c2665-106">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="c2665-107">[Sabitleme iyileştirmesi](copying-and-pinning.md)ile, bir blittable dizisi aynı apartman içindeki nesnelerle etkileşim kurarken bir ın/out parametresi olarak çalışmak üzere görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-107">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="c2665-108">Ancak, daha sonra kodu, platformlar arası ara sunucu oluşturmak için kullanılan bir tür kitaplığına dışa aktardığınızda ve bu kitaplık, çağrılarınızı gruplar arasında sıralamak için kullanılırsa, çağrılar parametre davranışındaki true değerine dönebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-108">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="c2665-109">Diziler doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki farklılıklar diğer blittable olmayan türlerden daha fazla bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="c2665-109">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="c2665-110">Yönetilen diziler</span><span class="sxs-lookup"><span data-stu-id="c2665-110">Managed Arrays</span></span>  
 <span data-ttu-id="c2665-111">Yönetilen dizi türleri farklılık gösterebilir; Ancak, <xref:System.Array?displayProperty=nameWithType> sınıfı tüm dizi türlerinin temel sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c2665-111">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="c2665-112">**System. Array** sınıfında, bir dizinin derecesini, uzunluğunu ve alt ve üst sınırlarını belirlemek için özellikler ve ayrıca, dizilere erişme, sıralama, arama, kopyalama ve oluşturma yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="c2665-112">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="c2665-113">Bu dizi türleri dinamiktir ve temel sınıf kitaplığında tanımlı bir statik türe sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="c2665-113">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="c2665-114">Öğe türü ve derecenin her birleşiminin ayrı bir dizi türü olarak düşünmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2665-114">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="c2665-115">Bu nedenle, tek boyutlu bir tamsayılar dizisi, Çift türlerden oluşan tek boyutlu bir diziden farklı türde.</span><span class="sxs-lookup"><span data-stu-id="c2665-115">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="c2665-116">Benzer şekilde iki boyutlu tamsayılar dizisi, tek boyutlu tamsayılar dizisinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c2665-116">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="c2665-117">Dizi sınırları, türler karşılaştırılırken düşünülmez.</span><span class="sxs-lookup"><span data-stu-id="c2665-117">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="c2665-118">Aşağıdaki tabloda gösterildiği gibi, yönetilen bir dizinin herhangi bir örneği belirli bir öğe türü, derece ve alt sınır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2665-118">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="c2665-119">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="c2665-119">Managed array type</span></span>|<span data-ttu-id="c2665-120">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="c2665-120">Element type</span></span>|<span data-ttu-id="c2665-121">Derece</span><span class="sxs-lookup"><span data-stu-id="c2665-121">Rank</span></span>|<span data-ttu-id="c2665-122">Alt sınır</span><span class="sxs-lookup"><span data-stu-id="c2665-122">Lower bound</span></span>|<span data-ttu-id="c2665-123">İmza gösterimi</span><span class="sxs-lookup"><span data-stu-id="c2665-123">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="c2665-124">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="c2665-124">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="c2665-125">Türe göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c2665-125">Specified by type.</span></span>|<span data-ttu-id="c2665-126">Derecesine göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c2665-126">Specified by rank.</span></span>|<span data-ttu-id="c2665-127">İsteğe bağlı olarak sınırlara göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-127">Optionally specified by bounds.</span></span>|<span data-ttu-id="c2665-128">*tür* **[** *n*,*d* **]**</span><span class="sxs-lookup"><span data-stu-id="c2665-128">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="c2665-129">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="c2665-129">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="c2665-130">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c2665-130">Unknown</span></span>|<span data-ttu-id="c2665-131">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c2665-131">Unknown</span></span>|<span data-ttu-id="c2665-132">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c2665-132">Unknown</span></span>|<span data-ttu-id="c2665-133">**System. Array**</span><span class="sxs-lookup"><span data-stu-id="c2665-133">**System.Array**</span></span>|  
|<span data-ttu-id="c2665-134">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="c2665-134">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="c2665-135">Türe göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c2665-135">Specified by type.</span></span>|<span data-ttu-id="c2665-136">1</span><span class="sxs-lookup"><span data-stu-id="c2665-136">1</span></span>|<span data-ttu-id="c2665-137">0</span><span class="sxs-lookup"><span data-stu-id="c2665-137">0</span></span>|<span data-ttu-id="c2665-138">*tür* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="c2665-138">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="c2665-139">Yönetilmeyen diziler</span><span class="sxs-lookup"><span data-stu-id="c2665-139">Unmanaged Arrays</span></span>  
 <span data-ttu-id="c2665-140">Yönetilmeyen diziler, sabit veya değişken uzunlukla birlikte, COM stili güvenli diziler veya C stili diziler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-140">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="c2665-141">Güvenli diziler, ilişkili dizi verilerinin türünü, derecesini ve sınırlarını taşıyan kendi kendine açıklayıcı dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="c2665-141">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="c2665-142">C stili diziler, sabit bir alt sınırı 0 olan tek boyutlu bir tür dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="c2665-142">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="c2665-143">Sıralama hizmeti, her iki dizi türü için sınırlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="c2665-143">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="c2665-144">Dizi parametrelerini .NET koduna geçirme</span><span class="sxs-lookup"><span data-stu-id="c2665-144">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="c2665-145">Hem C stili diziler hem de güvenli diziler, yönetilmeyen koddan güvenli bir dizi ya da C stili dizi olarak .NET koduna geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-145">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="c2665-146">Aşağıdaki tabloda, yönetilmeyen tür değeri ve içeri aktarılan tür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2665-146">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="c2665-147">Yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="c2665-147">Unmanaged type</span></span>|<span data-ttu-id="c2665-148">İçeri aktarılan tür</span><span class="sxs-lookup"><span data-stu-id="c2665-148">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="c2665-149">**SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c2665-149">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="c2665-150">**element_type_szarray\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="c2665-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="c2665-151">Derece = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="c2665-151">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="c2665-152">Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="c2665-152">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="c2665-153">Rank = 1 veya alt sınır = 0 olmayan güvenli diziler **Szarray**olarak sıralanamaz.</span><span class="sxs-lookup"><span data-stu-id="c2665-153">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="c2665-154">*Tür*  **[]**</span><span class="sxs-lookup"><span data-stu-id="c2665-154">*Type*  **[]**</span></span>|<span data-ttu-id="c2665-155">**element_type_szarray\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="c2665-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="c2665-156">Derece = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="c2665-156">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="c2665-157">Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="c2665-157">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="c2665-158">Güvenli diziler</span><span class="sxs-lookup"><span data-stu-id="c2665-158">Safe Arrays</span></span>  
 <span data-ttu-id="c2665-159">Bir tür kitaplığından bir .NET derlemesine bir güvenli dizi aktarıldığında, dizi bilinen bir türün ( **int**gibi) tek boyutlu dizisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c2665-159">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="c2665-160">Parametrelere uygulanan aynı tür dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2665-160">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="c2665-161">Örneğin, bir **BSTR** türündeki güvenli dizi, yönetilen dizelerin bir dizisi haline gelir ve bir dizi güvenli değişken yönetilen bir nesne dizisi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c2665-161">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="c2665-162">**SAFEARRAY** öğe türü tür kitaplığından yakalanır ve numaralandırmanın **SAFEARRAY** değerine kaydedilir <xref:System.Runtime.InteropServices.UnmanagedType> .</span><span class="sxs-lookup"><span data-stu-id="c2665-162">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="c2665-163">Güvenli dizinin derecesi ve sınırları tür kitaplığından belirlenemediğinden, derece 1 ' e eşit kabul edilir ve alt sınır 0 ' a eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-163">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="c2665-164">Sıralama ve sınırların, [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından üretilen yönetilen İmzada tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2665-164">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="c2665-165">Çalışma zamanında yönteme geçirilen derece farklıysa, bir oluşturulur <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> .</span><span class="sxs-lookup"><span data-stu-id="c2665-165">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="c2665-166">Çalışma zamanında geçirilen dizi türü farklıysa, bir oluşturulur <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> .</span><span class="sxs-lookup"><span data-stu-id="c2665-166">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="c2665-167">Aşağıdaki örnekte, yönetilen ve yönetilmeyen koddaki güvenli diziler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2665-167">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c2665-168">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-168">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="c2665-169">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-169">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c2665-170">Tlbimp.exe tarafından üretilen Yöntem imzası **element_type_szarray**yerine **element_type_array** bir öğe türü belirtmek için değiştirilirse, çok boyutlu veya sıfır dışında bağlantılı güvenli diziler yönetilen koda sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-170">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="c2665-171">Alternatif olarak, tüm dizileri nesne olarak içeri aktarmak için, **/sysarray** anahtarını Tlbimp.exe ile birlikte kullanabilirsiniz <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c2665-171">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="c2665-172">Geçirilen dizinin çok boyutlu olduğu bilindiğinde, Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyebilir ve sonra yeniden derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2665-172">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="c2665-173">MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c2665-173">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="c2665-174">C stili diziler</span><span class="sxs-lookup"><span data-stu-id="c2665-174">C-Style Arrays</span></span>  
 <span data-ttu-id="c2665-175">Bir C stili dizi bir tür kitaplığından .NET derlemesine aktarıldığında, dizi **element_type_szarray**dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c2665-175">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="c2665-176">Dizi öğesi türü tür kitaplığından belirlenir ve içeri aktarma sırasında korunur.</span><span class="sxs-lookup"><span data-stu-id="c2665-176">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="c2665-177">Parametrelere uygulanan aynı dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2665-177">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="c2665-178">Örneğin, **LPSTR** türünden oluşan bir dizi **dize** türü dizisi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c2665-178">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="c2665-179">Tlbimp.exe dizi öğesi türünü yakalar ve <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğini parametresine uygular.</span><span class="sxs-lookup"><span data-stu-id="c2665-179">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="c2665-180">Dizi derecesi 1 ' e eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-180">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="c2665-181">Sıra 1 ' den büyükse, dizi sütun birincil sırada tek boyutlu bir dizi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-181">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="c2665-182">Alt sınır her zaman 0 ' a eşittir.</span><span class="sxs-lookup"><span data-stu-id="c2665-182">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="c2665-183">Tür kitaplıklarında sabit veya değişken uzunlukta diziler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-183">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="c2665-184">Tlbimp.exe, tür kitaplıklarının değişken uzunluklu dizileri sıralamak için gereken bilgilerin olmadığından tür kitaplıklarından yalnızca sabit uzunluklu diziler alabilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-184">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="c2665-185">Sabit uzunluklu diziler ile, boyut tür kitaplığından içeri aktarılır ve parametreye uygulanan **MarshalAsAttribute** içinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-185">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="c2665-186">Aşağıdaki örnekte gösterildiği gibi, değişken uzunluklu diziler içeren tür kitaplıklarını el ile tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2665-186">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c2665-187">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-187">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="c2665-188">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-188">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c2665-189">Boyutu bir istemciye iletmek için arabirim tanım dili (IDL) kaynağındaki bir diziye **size_is** veya **length_is** özniteliklerini uygulayabilseniz de, Microsoft arabirim tanımlama dili (MIDL) derleyicisi bu bilgileri tür kitaplığına yaymaz.</span><span class="sxs-lookup"><span data-stu-id="c2665-189">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="c2665-190">Boyut bilinmeden, birlikte çalışma sıralama hizmeti dizi öğelerini sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="c2665-190">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="c2665-191">Sonuç olarak, değişken uzunluklu diziler başvuru bağımsız değişkenleri olarak içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="c2665-191">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="c2665-192">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-192">For example:</span></span>  
  
 <span data-ttu-id="c2665-193">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-193">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="c2665-194">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c2665-194">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c2665-195">Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyerek ve sonra yeniden derleyerek dizi boyutu ile Sıralayıcı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2665-195">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="c2665-196">MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c2665-196">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="c2665-197">Dizideki öğe sayısını göstermek için, <xref:System.Runtime.InteropServices.MarshalAsAttribute> türü yönetilen yöntem tanımının dizi parametresine aşağıdaki yöntemlerden biriyle uygulayın:</span><span class="sxs-lookup"><span data-stu-id="c2665-197">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="c2665-198">Dizideki öğe sayısını içeren başka bir parametre tanımla.</span><span class="sxs-lookup"><span data-stu-id="c2665-198">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="c2665-199">Parametreler, 0 numaralı ilk parametre ile başlayarak konuma göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-199">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
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
  
- <span data-ttu-id="c2665-200">Dizinin boyutunu bir sabit olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c2665-200">Define the size of the array as a constant.</span></span> <span data-ttu-id="c2665-201">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-201">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="c2665-202">Yönetilmeyen koddan yönetilen koda diziler hazırlama sırasında Sıralayıcı, dizi boyutunu belirlemede parametresiyle ilişkili **MarshalAsAttribute** denetler.</span><span class="sxs-lookup"><span data-stu-id="c2665-202">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="c2665-203">Dizi boyutu belirtilmemişse yalnızca bir öğe sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-203">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2665-204">**MarshalAsAttribute** yönetilen dizileri yönetilmeyen koda hazırlamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c2665-204">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="c2665-205">Bu yönde, dizi boyutu İnceleme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c2665-205">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="c2665-206">Yönetilen dizinin bir alt kümesini sıralama yöntemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c2665-206">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="c2665-207">Birlikte çalışma sıralayıcısı, bellek ayırmak ve almak için **CoTaskMemAlloc** ve **CoTaskMemFree** yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-207">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="c2665-208">Yönetilmeyen kod tarafından gerçekleştirilen bellek ayırma Ayrıca bu yöntemleri de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2665-208">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="c2665-209">Dizileri COM 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="c2665-209">Passing Arrays to COM</span></span>  
 <span data-ttu-id="c2665-210">Tüm yönetilen dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-210">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="c2665-211">Yönetilen türe ve ona uygulanan özniteliklere bağlı olarak, aşağıdaki tabloda gösterildiği gibi diziye bir güvenli dizi veya C stili dizi olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-211">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c2665-212">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="c2665-212">Managed array type</span></span>|<span data-ttu-id="c2665-213">Farklı olarak verildi</span><span class="sxs-lookup"><span data-stu-id="c2665-213">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="c2665-214">**element_type_szarray\*\*\*\*\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="c2665-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="c2665-215"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c2665-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c2665-216">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="c2665-216">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="c2665-217">Tür, İmzada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2665-217">Type is provided in the signature.</span></span> <span data-ttu-id="c2665-218">Rank her zaman 1, alt sınır her zaman 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="c2665-218">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="c2665-219">Boyut her zaman çalışma zamanında bilinirdi.</span><span class="sxs-lookup"><span data-stu-id="c2665-219">Size is always known at run time.</span></span>|  
|<span data-ttu-id="c2665-220">**element_type_array** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span><span class="sxs-lookup"><span data-stu-id="c2665-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="c2665-221">**UnmanagedType. SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c2665-221">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c2665-222">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="c2665-222">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="c2665-223">İmzada tür, derece, sınırlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2665-223">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="c2665-224">Boyut her zaman çalışma zamanında bilinirdi.</span><span class="sxs-lookup"><span data-stu-id="c2665-224">Size is always known at run time.</span></span>|  
|<span data-ttu-id="c2665-225">**element_type_class\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span><span class="sxs-lookup"><span data-stu-id="c2665-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span></span>|<span data-ttu-id="c2665-226">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="c2665-226">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="c2665-227">**UnmanagedType. SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c2665-227">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c2665-228">Tür, derece, sınır ve boyut her zaman çalışma zamanında bilinirler.</span><span class="sxs-lookup"><span data-stu-id="c2665-228">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="c2665-229">OLE Otomasyonunda LPSTR veya LPWSTR içeren yapıların dizileri ile ilgili bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="c2665-229">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="c2665-230">Bu nedenle, **dize** alanlarının **UnmanagedType. BSTR**olarak sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2665-230">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="c2665-231">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c2665-231">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="c2665-232">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="c2665-232">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="c2665-233">Bir **element_type_szarray** parametresi (tek boyutlu dizi) içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c2665-233">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="c2665-234">Aynı dönüştürme kuralları dizi öğesi türleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2665-234">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="c2665-235">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-235">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="c2665-236">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-236">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-237">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-237">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c2665-238">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-238">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="c2665-239">Güvenli dizilerin sıralaması her zaman 1 ' dir ve alt sınır her zaman 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="c2665-239">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="c2665-240">Boyut, çalışma zamanında geçirilmekte olan yönetilen dizinin boyutuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c2665-240">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="c2665-241">Dizi, özniteliği kullanılarak C stili bir dizi olarak da sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c2665-241">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c2665-242">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-242">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-243">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-243">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c2665-244">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-244">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="c2665-245">Sıralayıcı, diziyi sıralamak için gereken uzunluk bilgilerine sahip olsa da, dizi uzunluğu genellikle ayrı bir bağımsız değişken olarak geçirilir ve bu da uzunluğu aranan olarak iletmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2665-245">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="c2665-246">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="c2665-246">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="c2665-247">Bir **element_type_array** parametresi içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c2665-247">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="c2665-248">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-248">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="c2665-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-249">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-250">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-250">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c2665-251">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-251">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="c2665-252">Güvenli dizilerin derece, boyut ve sınırları, çalışma zamanında yönetilen dizinin özelliklerine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c2665-252">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="c2665-253">Dizi, özniteliği uygulanarak C stili bir dizi olarak da sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c2665-253">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c2665-254">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-254">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-255">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-255">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c2665-256">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-256">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="c2665-257">İç içe diziler sıralanamaz.</span><span class="sxs-lookup"><span data-stu-id="c2665-257">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="c2665-258">Örneğin, aşağıdaki imza [tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışarı aktarıldığında bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c2665-258">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-259">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-259">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="c2665-260">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="c2665-260">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="c2665-261">Bir parametre içeren bir yöntem bir <xref:System.Array?displayProperty=nameWithType> .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi bir **_array** arabirimine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c2665-261">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="c2665-262">Yönetilen dizinin içeriğine yalnızca **_array** arabiriminin yöntemleri ve özellikleri aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-262">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="c2665-263">**System. Array** , özniteliği kullanılarak bir **SAFEARRAY** olarak da sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c2665-263">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c2665-264">Güvenli bir dizi olarak sıralandığınızda, dizi öğeleri de çeşitler olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-264">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="c2665-265">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c2665-265">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c2665-266">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-266">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c2665-267">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c2665-267">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="c2665-268">Yapılar içindeki diziler</span><span class="sxs-lookup"><span data-stu-id="c2665-268">Arrays within Structures</span></span>  
 <span data-ttu-id="c2665-269">Yönetilmeyen yapılar, gömülü diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-269">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="c2665-270">Varsayılan olarak, bu katıştırılmış dizi alanları bir SAFEARRAY olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c2665-270">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="c2665-271">Aşağıdaki örnekte, `s1` doğrudan yapının içinde ayrılmış bir katıştırılmış dizidir.</span><span class="sxs-lookup"><span data-stu-id="c2665-271">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="c2665-272">Yönetilmeyen Gösterim</span><span class="sxs-lookup"><span data-stu-id="c2665-272">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="c2665-273">Diziler, <xref:System.Runtime.InteropServices.UnmanagedType> alanı ayarlamanızı gerektiren olarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c2665-273">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="c2665-274">Boyut yalnızca bir sabit olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c2665-274">The size can be set only as a constant.</span></span> <span data-ttu-id="c2665-275">Aşağıdaki kod, karşılık gelen yönetilen tanımını gösterir `MyStruct` .</span><span class="sxs-lookup"><span data-stu-id="c2665-275">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2665-276">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2665-276">See also</span></span>

- [<span data-ttu-id="c2665-277">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="c2665-277">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="c2665-278">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="c2665-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="c2665-279">[Yönlü öznitelikler](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c2665-279">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="c2665-280">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="c2665-280">Copying and Pinning</span></span>](copying-and-pinning.md)
