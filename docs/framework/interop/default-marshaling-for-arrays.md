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
ms.openlocfilehash: 8505f4c742fb002be249ab069708f7f768c672df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123570"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="c065a-102">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="c065a-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="c065a-103">Tamamen yönetilen koddan oluşan bir uygulamada, ortak dil çalışma zamanı dizi türlerini ın/out parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c065a-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="c065a-104">Buna karşılık, birlikte çalışma sıralayıcısı varsayılan olarak parametre olarak bir diziyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="c065a-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="c065a-105">[Sabitleme iyileştirmesi](copying-and-pinning.md)ile, bir blittable dizisi aynı apartman içindeki nesnelerle etkileşim kurarken bir ın/out parametresi olarak çalışmak üzere görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="c065a-106">Ancak, daha sonra kodu, platformlar arası ara sunucu oluşturmak için kullanılan bir tür kitaplığına dışa aktardığınızda ve bu kitaplık, çağrılarınızı gruplar arasında sıralamak için kullanılırsa, çağrılar parametre davranışındaki true değerine dönebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="c065a-107">Diziler doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki farklılıklar diğer blittable olmayan türlerden daha fazla bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="c065a-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="c065a-108">Yönetilen diziler</span><span class="sxs-lookup"><span data-stu-id="c065a-108">Managed Arrays</span></span>  
 <span data-ttu-id="c065a-109">Yönetilen dizi türleri farklılık gösterebilir; Ancak, <xref:System.Array?displayProperty=nameWithType> sınıfı tüm dizi türlerinin temel sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c065a-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="c065a-110">**System. Array** sınıfında, bir dizinin derecesini, uzunluğunu ve alt ve üst sınırlarını belirlemek için özellikler ve ayrıca, dizilere erişme, sıralama, arama, kopyalama ve oluşturma yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="c065a-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="c065a-111">Bu dizi türleri dinamiktir ve temel sınıf kitaplığında tanımlı bir statik türe sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="c065a-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="c065a-112">Öğe türü ve derecenin her birleşiminin ayrı bir dizi türü olarak düşünmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c065a-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="c065a-113">Bu nedenle, tek boyutlu bir tamsayılar dizisi, Çift türlerden oluşan tek boyutlu bir diziden farklı türde.</span><span class="sxs-lookup"><span data-stu-id="c065a-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="c065a-114">Benzer şekilde iki boyutlu tamsayılar dizisi, tek boyutlu tamsayılar dizisinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c065a-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="c065a-115">Dizi sınırları, türler karşılaştırılırken düşünülmez.</span><span class="sxs-lookup"><span data-stu-id="c065a-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="c065a-116">Aşağıdaki tabloda gösterildiği gibi, yönetilen bir dizinin herhangi bir örneği belirli bir öğe türü, derece ve alt sınır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c065a-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="c065a-117">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="c065a-117">Managed array type</span></span>|<span data-ttu-id="c065a-118">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="c065a-118">Element type</span></span>|<span data-ttu-id="c065a-119">Sırası</span><span class="sxs-lookup"><span data-stu-id="c065a-119">Rank</span></span>|<span data-ttu-id="c065a-120">Alt sınır</span><span class="sxs-lookup"><span data-stu-id="c065a-120">Lower bound</span></span>|<span data-ttu-id="c065a-121">İmza gösterimi</span><span class="sxs-lookup"><span data-stu-id="c065a-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="c065a-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="c065a-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="c065a-123">Türe göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c065a-123">Specified by type.</span></span>|<span data-ttu-id="c065a-124">Derecesine göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c065a-124">Specified by rank.</span></span>|<span data-ttu-id="c065a-125">İsteğe bağlı olarak sınırlara göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="c065a-126">*tür* **[** *n*,*d* **]**</span><span class="sxs-lookup"><span data-stu-id="c065a-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="c065a-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="c065a-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="c065a-128">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c065a-128">Unknown</span></span>|<span data-ttu-id="c065a-129">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c065a-129">Unknown</span></span>|<span data-ttu-id="c065a-130">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="c065a-130">Unknown</span></span>|<span data-ttu-id="c065a-131">**System. Array**</span><span class="sxs-lookup"><span data-stu-id="c065a-131">**System.Array**</span></span>|  
|<span data-ttu-id="c065a-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="c065a-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="c065a-133">Türe göre belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c065a-133">Specified by type.</span></span>|<span data-ttu-id="c065a-134">1\.</span><span class="sxs-lookup"><span data-stu-id="c065a-134">1</span></span>|<span data-ttu-id="c065a-135">0</span><span class="sxs-lookup"><span data-stu-id="c065a-135">0</span></span>|<span data-ttu-id="c065a-136">*tür* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="c065a-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="c065a-137">Yönetilmeyen diziler</span><span class="sxs-lookup"><span data-stu-id="c065a-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="c065a-138">Yönetilmeyen diziler, sabit veya değişken uzunlukla birlikte, COM stili güvenli diziler veya C stili diziler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="c065a-139">Güvenli diziler, ilişkili dizi verilerinin türünü, derecesini ve sınırlarını taşıyan kendi kendine açıklayıcı dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="c065a-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="c065a-140">C stili diziler, sabit bir alt sınırı 0 olan tek boyutlu bir tür dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="c065a-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="c065a-141">Sıralama hizmeti, her iki dizi türü için sınırlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="c065a-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="c065a-142">Dizi parametrelerini .NET koduna geçirme</span><span class="sxs-lookup"><span data-stu-id="c065a-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="c065a-143">Hem C stili diziler hem de güvenli diziler, yönetilmeyen koddan güvenli bir dizi ya da C stili dizi olarak .NET koduna geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="c065a-144">Aşağıdaki tabloda, yönetilmeyen tür değeri ve içeri aktarılan tür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c065a-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="c065a-145">Yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="c065a-145">Unmanaged type</span></span>|<span data-ttu-id="c065a-146">İçeri aktarılan tür</span><span class="sxs-lookup"><span data-stu-id="c065a-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="c065a-147">**SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c065a-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="c065a-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="c065a-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="c065a-149">Derece = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="c065a-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="c065a-150">Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="c065a-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="c065a-151">Rank = 1 veya alt sınır = 0 olmayan güvenli diziler **Szarray**olarak sıralanamaz.</span><span class="sxs-lookup"><span data-stu-id="c065a-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="c065a-152">*Tür*  **[]**</span><span class="sxs-lookup"><span data-stu-id="c065a-152">*Type*  **[]**</span></span>|<span data-ttu-id="c065a-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="c065a-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="c065a-154">Derece = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="c065a-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="c065a-155">Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir.</span><span class="sxs-lookup"><span data-stu-id="c065a-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="c065a-156">Güvenli diziler</span><span class="sxs-lookup"><span data-stu-id="c065a-156">Safe Arrays</span></span>  
 <span data-ttu-id="c065a-157">Bir tür kitaplığından bir .NET derlemesine bir güvenli dizi aktarıldığında, dizi bilinen bir türün ( **int**gibi) tek boyutlu dizisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c065a-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="c065a-158">Parametrelere uygulanan aynı tür dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c065a-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="c065a-159">Örneğin, bir **BSTR** türündeki güvenli dizi, yönetilen dizelerin bir dizisi haline gelir ve bir dizi güvenli değişken yönetilen bir nesne dizisi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c065a-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="c065a-160">**SAFEARRAY** öğe türü tür kitaplığından yakalanır ve <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmanın **SAFEARRAY** değerine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="c065a-161">Güvenli dizinin derecesi ve sınırları tür kitaplığından belirlenemediğinden, derece 1 ' e eşit kabul edilir ve alt sınır 0 ' a eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="c065a-162">Sıralama ve sınırların, [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından üretilen yönetilen İmzada tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c065a-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="c065a-163">Çalışma zamanında yönteme geçirilen derece farklıysa bir <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c065a-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="c065a-164">Çalışma zamanında geçirilen dizi türü farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c065a-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="c065a-165">Aşağıdaki örnekte, yönetilen ve yönetilmeyen koddaki güvenli diziler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c065a-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c065a-166">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-166">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="c065a-167">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-167">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c065a-168">Tlbimp. exe tarafından üretilen Yöntem imzası, **element_type_szarray**yerine **element_type_array** öğe türünü gösterecek şekilde değiştirilirse, çok boyutlu veya sıfır dışında bağlantılı güvenli diziler yönetilen koda sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="c065a-169">Alternatif olarak, tüm dizileri <xref:System.Array?displayProperty=nameWithType> nesne olarak içeri aktarmak için **/sysarray** anahtarını Tlbimp. exe ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c065a-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="c065a-170">Geçirilen dizinin çok boyutlu olduğu bilindiğinde, Tlbimp. exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyebilir ve sonra yeniden derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c065a-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="c065a-171">MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c065a-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="c065a-172">C stili diziler</span><span class="sxs-lookup"><span data-stu-id="c065a-172">C-Style Arrays</span></span>  
 <span data-ttu-id="c065a-173">Bir C stili dizi bir tür kitaplığından .NET derlemesine aktarıldığında, dizi **element_type_szarray**olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c065a-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="c065a-174">Dizi öğesi türü tür kitaplığından belirlenir ve içeri aktarma sırasında korunur.</span><span class="sxs-lookup"><span data-stu-id="c065a-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="c065a-175">Parametrelere uygulanan aynı dönüştürme kuralları dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c065a-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="c065a-176">Örneğin, **LPSTR** türünden oluşan bir dizi **dize** türü dizisi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c065a-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="c065a-177">Tlbimp. exe, dizi öğesi türünü yakalar ve <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğini parametresine uygular.</span><span class="sxs-lookup"><span data-stu-id="c065a-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="c065a-178">Dizi derecesi 1 ' e eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="c065a-179">Sıra 1 ' den büyükse, dizi sütun birincil sırada tek boyutlu bir dizi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="c065a-180">Alt sınır her zaman 0 ' a eşittir.</span><span class="sxs-lookup"><span data-stu-id="c065a-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="c065a-181">Tür kitaplıklarında sabit veya değişken uzunlukta diziler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="c065a-182">Tür kitaplıklarında değişken uzunluklu dizileri sıralamak için gereken bilgiler bulunmadığından, Tlbimp. exe yalnızca tür kitaplıklarından sabit uzunluklu diziler alabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="c065a-183">Sabit uzunluklu diziler ile, boyut tür kitaplığından içeri aktarılır ve parametreye uygulanan **MarshalAsAttribute** içinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="c065a-184">Aşağıdaki örnekte gösterildiği gibi, değişken uzunluklu diziler içeren tür kitaplıklarını el ile tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c065a-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c065a-185">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-185">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="c065a-186">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-186">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c065a-187">Boyutu bir istemciye iletmek için, bir arabirim tanım dili (IDL) kaynağındaki bir **diziye veya** **length_is** özniteliklerini uygulayabilseniz de, Microsoft arabirim tanımlama dili (MIDL) derleyicisi bunu yayılmaz tür kitaplığına ilişkin bilgiler.</span><span class="sxs-lookup"><span data-stu-id="c065a-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="c065a-188">Boyut bilinmeden, birlikte çalışma sıralama hizmeti dizi öğelerini sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="c065a-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="c065a-189">Sonuç olarak, değişken uzunluklu diziler başvuru bağımsız değişkenleri olarak içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="c065a-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="c065a-190">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-190">For example:</span></span>  
  
 <span data-ttu-id="c065a-191">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-191">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="c065a-192">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="c065a-192">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="c065a-193">Tlbimp. exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyerek ve sonra yeniden derleyerek dizi boyutu ile Sıralayıcı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c065a-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="c065a-194">MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c065a-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="c065a-195">Dizideki öğe sayısını göstermek için <xref:System.Runtime.InteropServices.MarshalAsAttribute> türünü yönetilen yöntem tanımının dizi parametresine aşağıdaki yöntemlerden biriyle uygulayın:</span><span class="sxs-lookup"><span data-stu-id="c065a-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="c065a-196">Dizideki öğe sayısını içeren başka bir parametre tanımla.</span><span class="sxs-lookup"><span data-stu-id="c065a-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="c065a-197">Parametreler, 0 numaralı ilk parametre ile başlayarak konuma göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
- <span data-ttu-id="c065a-198">Dizinin boyutunu bir sabit olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c065a-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="c065a-199">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="c065a-200">Yönetilmeyen koddan yönetilen koda diziler hazırlama sırasında Sıralayıcı, dizi boyutunu belirlemede parametresiyle ilişkili **MarshalAsAttribute** denetler.</span><span class="sxs-lookup"><span data-stu-id="c065a-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="c065a-201">Dizi boyutu belirtilmemişse yalnızca bir öğe sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c065a-202">**MarshalAsAttribute** yönetilen dizileri yönetilmeyen koda hazırlamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c065a-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="c065a-203">Bu yönde, dizi boyutu İnceleme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c065a-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="c065a-204">Yönetilen dizinin bir alt kümesini sıralama yöntemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c065a-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="c065a-205">Birlikte çalışma sıralayıcısı, bellek ayırmak ve almak için **CoTaskMemAlloc** ve **CoTaskMemFree** yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="c065a-206">Yönetilmeyen kod tarafından gerçekleştirilen bellek ayırma Ayrıca bu yöntemleri de kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c065a-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="c065a-207">Dizileri COM 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="c065a-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="c065a-208">Tüm yönetilen dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="c065a-209">Yönetilen türe ve ona uygulanan özniteliklere bağlı olarak, aşağıdaki tabloda gösterildiği gibi diziye bir güvenli dizi veya C stili dizi olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c065a-210">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="c065a-210">Managed array type</span></span>|<span data-ttu-id="c065a-211">Farklı olarak verildi</span><span class="sxs-lookup"><span data-stu-id="c065a-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="c065a-212">**ELEMENT_TYPE_SZARRAY** **\<** *türü* **>**</span><span class="sxs-lookup"><span data-stu-id="c065a-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="c065a-213"><xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c065a-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c065a-214">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="c065a-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="c065a-215">Tür, İmzada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c065a-215">Type is provided in the signature.</span></span> <span data-ttu-id="c065a-216">Rank her zaman 1, alt sınır her zaman 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="c065a-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="c065a-217">Boyut her zaman çalışma zamanında bilinirdi.</span><span class="sxs-lookup"><span data-stu-id="c065a-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="c065a-218">**ELEMENT_TYPE_ARRAY** **\<** *türü* **>** **\<** *Rank* **>** [ **\<** *sınır* **>** ]</span><span class="sxs-lookup"><span data-stu-id="c065a-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="c065a-219">**UnmanagedType. SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c065a-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c065a-220">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="c065a-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="c065a-221">İmzada tür, derece, sınırlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c065a-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="c065a-222">Boyut her zaman çalışma zamanında bilinirdi.</span><span class="sxs-lookup"><span data-stu-id="c065a-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="c065a-223">**ELEMENT_TYPE_CLASS** **\<** <xref:System.Array?displayProperty=nameWithType> **>**</span><span class="sxs-lookup"><span data-stu-id="c065a-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="c065a-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="c065a-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="c065a-225">**UnmanagedType. SAFEARRAY (** *tür* **)**</span><span class="sxs-lookup"><span data-stu-id="c065a-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="c065a-226">Tür, derece, sınır ve boyut her zaman çalışma zamanında bilinirler.</span><span class="sxs-lookup"><span data-stu-id="c065a-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="c065a-227">OLE Otomasyonunda LPSTR veya LPWSTR içeren yapıların dizileri ile ilgili bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="c065a-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="c065a-228">Bu nedenle, **dize** alanlarının **UnmanagedType. BSTR**olarak sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c065a-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="c065a-229">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c065a-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="c065a-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="c065a-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="c065a-231">Bir **element_type_szarray** parametresi (tek boyutlu dizi) içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c065a-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="c065a-232">Aynı dönüştürme kuralları dizi öğesi türleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c065a-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="c065a-233">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="c065a-234">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-235">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c065a-236">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-236">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="c065a-237">Güvenli dizilerin sıralaması her zaman 1 ' dir ve alt sınır her zaman 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="c065a-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="c065a-238">Boyut, çalışma zamanında geçirilmekte olan yönetilen dizinin boyutuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c065a-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="c065a-239">Dizi, <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği kullanılarak C stili bir dizi olarak da sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c065a-240">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-241">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-241">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c065a-242">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-242">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="c065a-243">Sıralayıcı, diziyi sıralamak için gereken uzunluk bilgilerine sahip olsa da, dizi uzunluğu genellikle ayrı bir bağımsız değişken olarak geçirilir ve bu da uzunluğu aranan olarak iletmiştir.</span><span class="sxs-lookup"><span data-stu-id="c065a-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="c065a-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="c065a-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="c065a-245">Bir **element_type_array** parametresi içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c065a-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="c065a-246">Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="c065a-247">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-248">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c065a-249">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-249">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="c065a-250">Güvenli dizilerin derece, boyut ve sınırları, çalışma zamanında yönetilen dizinin özelliklerine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c065a-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="c065a-251">Dizi, <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği uygulanarak C stili bir dizi olarak da sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c065a-252">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-253">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-253">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c065a-254">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-254">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="c065a-255">İç içe diziler sıralanamaz.</span><span class="sxs-lookup"><span data-stu-id="c065a-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="c065a-256">Örneğin, aşağıdaki imza [tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışarı aktarıldığında bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c065a-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-257">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="c065a-258">ELEMENT_TYPE_CLASS \<System. Array ></span><span class="sxs-lookup"><span data-stu-id="c065a-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="c065a-259">Bir <xref:System.Array?displayProperty=nameWithType> parametresi içeren bir yöntem bir .NET derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi bir **_array** arabirimine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c065a-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="c065a-260">Yönetilen dizinin içeriğine yalnızca **_array** arabiriminin Yöntemler ve özellikleri aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="c065a-261">**System. Array** , <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği kullanılarak bir **SAFEARRAY** olarak da sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="c065a-262">Güvenli bir dizi olarak sıralandığınızda, dizi öğeleri de çeşitler olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="c065a-263">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c065a-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="c065a-264">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="c065a-265">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="c065a-265">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="c065a-266">Yapılar içindeki diziler</span><span class="sxs-lookup"><span data-stu-id="c065a-266">Arrays within Structures</span></span>  
 <span data-ttu-id="c065a-267">Yönetilmeyen yapılar, gömülü diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="c065a-268">Varsayılan olarak, bu katıştırılmış dizi alanları bir SAFEARRAY olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c065a-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="c065a-269">Aşağıdaki örnekte, `s1` doğrudan yapının içinde ayrılmış bir katıştırılmış dizidir.</span><span class="sxs-lookup"><span data-stu-id="c065a-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="c065a-270">Yönetilmeyen Gösterim</span><span class="sxs-lookup"><span data-stu-id="c065a-270">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="c065a-271">Diziler, <xref:System.Runtime.InteropServices.MarshalAsAttribute> alanını ayarlamanızı gerektiren <xref:System.Runtime.InteropServices.UnmanagedType>olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="c065a-272">Boyut yalnızca bir sabit olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c065a-272">The size can be set only as a constant.</span></span> <span data-ttu-id="c065a-273">Aşağıdaki kod, `MyStruct`karşılık gelen yönetilen tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c065a-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c065a-274">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c065a-274">See also</span></span>

- [<span data-ttu-id="c065a-275">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="c065a-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="c065a-276">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="c065a-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="c065a-277">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c065a-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="c065a-278">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="c065a-278">Copying and Pinning</span></span>](copying-and-pinning.md)
