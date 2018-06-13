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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05ac1016710109110c3ff9d0d318a71fe0827f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393156"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="6fdff-102">Diziler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="6fdff-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="6fdff-103">Tamamen yönetilen kod oluşan bir uygulamada, ortak dil çalışma zamanı dizi türleri olarak In/Out parametreleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="6fdff-104">Buna karşılık, birlikte çalışabilirlik Sıralayıcı parametreleri olduğu gibi bir dizi varsayılan olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="6fdff-105">İle [sabitleme iyileştirme](copying-and-pinning.md), blittable dizi olarak bir giriş/çıkış parametresi aynı grup nesneleri ile kullanılırken çalışması için yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="6fdff-106">Ancak, makineler arası proxy oluşturmak için kullanılan bir tür kitaplığı daha sonra kodu verme ve bu kitaplık aramalarınız grupların hazırlamak için kullanılır, çağrı parametresi davranış true için geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="6fdff-107">Diziler doğası gereği karmaşık ve diğer kopyalanamaz türler daha fazla bilgi yönetilen ve yönetilmeyen diziler arasındaki farklılıklar garanti.</span><span class="sxs-lookup"><span data-stu-id="6fdff-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span> <span data-ttu-id="6fdff-108">Bu konu, dizileri sıralama hakkında aşağıdaki bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="6fdff-108">This topic provides the following information on marshaling arrays:</span></span>  
  
-   [<span data-ttu-id="6fdff-109">Yönetilen diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-109">Managed Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [<span data-ttu-id="6fdff-110">Yönetilmeyen diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-110">Unmanaged Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [<span data-ttu-id="6fdff-111">.NET kodu için dizi parametreleri geçirme</span><span class="sxs-lookup"><span data-stu-id="6fdff-111">Passing Array Parameters to .NET Code</span></span>](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [<span data-ttu-id="6fdff-112">COM dizileri geçirme</span><span class="sxs-lookup"><span data-stu-id="6fdff-112">Passing Arrays to COM</span></span>](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a><span data-ttu-id="6fdff-113">Yönetilen diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-113">Managed Arrays</span></span>  
 <span data-ttu-id="6fdff-114">Dizi türleri değişebilir yönetilen; Ancak, <xref:System.Array?displayProperty=nameWithType> tüm dizi türleri temel sınıfını bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-114">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="6fdff-115">**System.Array** sınıfı derece, uzunluğu ve alt ve üst sınırları erişmek, sıralama, arama, kopyalama ve diziler oluşturma yöntemleri yanı sıra, bir dizi belirlemek için özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-115">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="6fdff-116">Bu dizi türleri dinamik ve temel sınıf kitaplığı'nda tanımlanan karşılık gelen bir statik türüne sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6fdff-116">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="6fdff-117">Her öğe türü ve sıra birleşimi dizi ayrı bir türü olarak düşünmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-117">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="6fdff-118">Bu nedenle, bir tek boyutlu tamsayı çift türlerinin tek boyutlu dizi daha farklı bir tür dizisidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-118">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="6fdff-119">Benzer şekilde tamsayıların iki boyutlu bir dizi tek boyutlu tamsayı diziden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-119">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="6fdff-120">Dizinin sınırları türleri karşılaştırılırken dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-120">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="6fdff-121">Aşağıdaki tabloda gösterildiği gibi yönetilen bir dizi herhangi bir örneğini bir özel öğe türü, derece ve alt sınır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-121">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="6fdff-122">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="6fdff-122">Managed array type</span></span>|<span data-ttu-id="6fdff-123">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="6fdff-123">Element type</span></span>|<span data-ttu-id="6fdff-124">RANK</span><span class="sxs-lookup"><span data-stu-id="6fdff-124">Rank</span></span>|<span data-ttu-id="6fdff-125">Alt sınır</span><span class="sxs-lookup"><span data-stu-id="6fdff-125">Lower bound</span></span>|<span data-ttu-id="6fdff-126">İmza gösterimi</span><span class="sxs-lookup"><span data-stu-id="6fdff-126">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="6fdff-127">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="6fdff-127">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="6fdff-128">Türü tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="6fdff-128">Specified by type.</span></span>|<span data-ttu-id="6fdff-129">RANK tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="6fdff-129">Specified by rank.</span></span>|<span data-ttu-id="6fdff-130">İsteğe bağlı olarak sınırları tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="6fdff-130">Optionally specified by bounds.</span></span>|<span data-ttu-id="6fdff-131">*tür* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="6fdff-131">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="6fdff-132">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="6fdff-132">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="6fdff-133">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="6fdff-133">Unknown</span></span>|<span data-ttu-id="6fdff-134">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="6fdff-134">Unknown</span></span>|<span data-ttu-id="6fdff-135">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="6fdff-135">Unknown</span></span>|<span data-ttu-id="6fdff-136">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="6fdff-136">**System.Array**</span></span>|  
|<span data-ttu-id="6fdff-137">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="6fdff-137">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="6fdff-138">Türü tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="6fdff-138">Specified by type.</span></span>|<span data-ttu-id="6fdff-139">1.</span><span class="sxs-lookup"><span data-stu-id="6fdff-139">1</span></span>|<span data-ttu-id="6fdff-140">0</span><span class="sxs-lookup"><span data-stu-id="6fdff-140">0</span></span>|<span data-ttu-id="6fdff-141">*tür* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="6fdff-141">*type* **[** *n* **]**</span></span>|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a><span data-ttu-id="6fdff-142">Yönetilmeyen diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-142">Unmanaged Arrays</span></span>  
 <span data-ttu-id="6fdff-143">COM Stili güvenli dizileri ya da sabit veya değişken uzunluğu ile C türü dizileri bunun yönetilmeyen dizidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-143">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="6fdff-144">Güvenli diziler türü, derece ve ilişkili dizi veri sınırları taşımak dizileri otomatik olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fdff-144">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="6fdff-145">C türü, sabit bir alt sınırı 0 ile yazılmış tek boyutlu diziler dizidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-145">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="6fdff-146">Hazırlama Hizmeti her iki tür diziler için destek sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-146">The marshaling service has limited support for both types of arrays.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="6fdff-147">.NET kodu için dizi parametreleri geçirme</span><span class="sxs-lookup"><span data-stu-id="6fdff-147">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="6fdff-148">C türü diziler ve güvenli diziler .NET kodu için güvenli diziye veya C tarzı dizisi olarak yönetilmeyen koddan geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-148">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="6fdff-149">Aşağıdaki tabloda, yönetilmeyen tür değeri ve içeri aktarılan türü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-149">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="6fdff-150">Yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="6fdff-150">Unmanaged type</span></span>|<span data-ttu-id="6fdff-151">İçeri aktarılan türü</span><span class="sxs-lookup"><span data-stu-id="6fdff-151">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="6fdff-152">**SafeArray (** *türü* **)**</span><span class="sxs-lookup"><span data-stu-id="6fdff-152">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="6fdff-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="6fdff-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="6fdff-154">RANK = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="6fdff-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="6fdff-155">Boyutu, yalnızca yönetilen imzada sağladıysanız denir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-155">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="6fdff-156">Rank olmayan güvenli diziler = 1 ya da alt sınır = 0 olamaz sıralanmış olarak **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-156">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="6fdff-157">*Tür***]**</span><span class="sxs-lookup"><span data-stu-id="6fdff-157">*Type*  **[]**</span></span>|<span data-ttu-id="6fdff-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="6fdff-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="6fdff-159">RANK = 1, alt sınır = 0.</span><span class="sxs-lookup"><span data-stu-id="6fdff-159">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="6fdff-160">Boyutu, yalnızca yönetilen imzada sağladıysanız denir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-160">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="6fdff-161">Güvenli diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-161">Safe Arrays</span></span>  
 <span data-ttu-id="6fdff-162">Bir .NET derlemesi için güvenli diziye bir tür kitaplığından içeri aktarıldığında dizi bilinen bir türde tek boyutlu bir diziye dönüştürülür (gibi **int**).</span><span class="sxs-lookup"><span data-stu-id="6fdff-162">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="6fdff-163">Parametreleri uygulamak aynı tür dönüştürme kurallarını dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-163">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="6fdff-164">Örneğin, güvenli bir dizi **BSTR** türleri yönetilen dizisini olur ve bir yönetilen nesneler dizisi güvenli dizisi olur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-164">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="6fdff-165">**SAFEARRAY** öğe türü tür kitaplığından yakalanan ve kaydedilen **SAFEARRAY** değerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6fdff-165">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="6fdff-166">Rank ve güvenli dizinin sınırları tür kitaplığından belirlenemediğinden, derecesini eşit 1 olarak kabul edilir ve alt sınırı eşit 0 olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-166">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="6fdff-167">Rank ve sınırları tarafından üretilen yönetilen imza tanımlanmalıdır [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="6fdff-167">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="6fdff-168">Çalışma zamanında yönteme geçirilen derece farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-168">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="6fdff-169">Dizi türü çalışma zamanında aktarılırsa farklıdır, bir <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-169">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="6fdff-170">Aşağıdaki örnek, yönetilen ve yönetilmeyen kodunda güvenli diziler gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-170">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="6fdff-171">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-171">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="6fdff-172">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-172">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="6fdff-173">Çok boyutlu veya sınırı sıfır olmayan güvenli diziler sıralanmış yönetilen koda Tlbimp.exe tarafından üretilen yöntem imzası bir öğe türünü belirtmek için değiştirilirse **ELEMENT_TYPE_ARRAY** yerine **ELEMENT_ TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-173">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="6fdff-174">Alternatif olarak, kullanabileceğiniz **/sysarray** tüm dizileri olarak almak için Tlbimp.exe anahtarı <xref:System.Array?displayProperty=nameWithType> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6fdff-174">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="6fdff-175">Çok boyutlu geçirilen dizi olduğu bilinen durumlarda Ara dili (MSIL) kod üretilen Microsoft Tlbimp.exe tarafından düzenleyin ve yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="6fdff-175">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="6fdff-176">MSIL kodu değiştirme hakkında daha fazla bilgi için bkz [çalışma zamanı aranabilir sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6fdff-176">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="6fdff-177">C türü diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-177">C-Style Arrays</span></span>  
 <span data-ttu-id="6fdff-178">C türü dizi bir .NET derlemesi bir tür kitaplığından içeri aktarıldığında dizi dönüştürülür **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-178">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="6fdff-179">Dizi öğesi türü tür kitaplığından belirlenir ve içeri aktarma sırasında korunur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-179">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="6fdff-180">Parametreleri uygulamak aynı dönüştürme kurallarını dizi öğeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-180">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="6fdff-181">Örneğin, bir dizi **LPStr** türleri dizisi hale **dize** türleri.</span><span class="sxs-lookup"><span data-stu-id="6fdff-181">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="6fdff-182">Tlbimp.exe dizi öğesi türü yakalar ve geçerlidir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği parametresi.</span><span class="sxs-lookup"><span data-stu-id="6fdff-182">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="6fdff-183">Dizi sıralaması 1'e eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-183">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="6fdff-184">Derece 1'den büyükse, dizi sütun öncelikli bir sırada tek boyutlu bir dizi olarak sıralanmış olduğundan.</span><span class="sxs-lookup"><span data-stu-id="6fdff-184">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="6fdff-185">Alt sınır her zaman 0'a eşit.</span><span class="sxs-lookup"><span data-stu-id="6fdff-185">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="6fdff-186">Tür kitaplıkları sabit veya değişken uzunlukta diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-186">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="6fdff-187">Tür kitaplıkları değişken uzunlukta diziler hazırlamak için gereken bilgileri bulunmadığından Tlbimp.exe tür kitaplıklarından yalnızca sabit uzunlukta diziler içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-187">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="6fdff-188">Sabit uzunluklu dizilerle boyutu tür kitaplığından içeri aktarıldı ve içinde yakalanan **MarshalAsAttribute** parametresi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-188">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="6fdff-189">Değişken uzunlukta diziler içeren tür kitaplıklarının, aşağıdaki örnekte gösterildiği gibi el ile tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="6fdff-189">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="6fdff-190">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-190">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="6fdff-191">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-191">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="6fdff-192">Geçerli olabilir ancak **size_is** veya **length_is** arabirimi tanım dili (IDL) kaynak boyutu bir istemci, Microsoft arabirimi tanım dili (MIDL) iletmek için bir dizi öznitelikleri derleyici tür kitaplığı için bu bilgileri dağıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-192">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="6fdff-193">Hizmet hazırlama birlikte çalışabilirliği boyutu bilmeden dizi öğeleri sıralanamıyor.</span><span class="sxs-lookup"><span data-stu-id="6fdff-193">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="6fdff-194">Sonuç olarak, değişken uzunlukta diziler başvuru bağımsız değişken olarak içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-194">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="6fdff-195">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-195">For example:</span></span>  
  
 <span data-ttu-id="6fdff-196">**Yönetilmeyen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-196">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="6fdff-197">**Yönetilen imza**</span><span class="sxs-lookup"><span data-stu-id="6fdff-197">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="6fdff-198">Ara dil (MSIL) kodu üretilen Microsoft Tlbimp.exe tarafından düzenleme ve daha sonra yeniden derlenmesi dizi boyutuyla Sıralayıcı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-198">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="6fdff-199">MSIL kodu değiştirme hakkında daha fazla bilgi için bkz [çalışma zamanı aranabilir sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6fdff-199">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span></span> <span data-ttu-id="6fdff-200">Dizideki öğelerin sayısını belirtmek için uygulamanız <xref:System.Runtime.InteropServices.MarshalAsAttribute> Yönetilen yöntemi tanımı'nda aşağıdaki yollardan biriyle dizi parametre türü:</span><span class="sxs-lookup"><span data-stu-id="6fdff-200">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="6fdff-201">Dizideki öğelerin sayısını içeren başka bir parametre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6fdff-201">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="6fdff-202">Parametreler, birinci parametreyle başlangıç numarası 0 konuma göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-202">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
-   <span data-ttu-id="6fdff-203">Dizinin boyutu bir sabit değer olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6fdff-203">Define the size of the array as a constant.</span></span> <span data-ttu-id="6fdff-204">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-204">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="6fdff-205">Yönetilmeyen koddan yönetilen koda dizileri sıralama sırasında Sıralayıcı denetler **MarshalAsAttribute** dizi boyutu belirlemek için parametre ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="6fdff-205">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="6fdff-206">Dizi boyutu belirtilmezse, yalnızca tek bir öğe başvuruya.</span><span class="sxs-lookup"><span data-stu-id="6fdff-206">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fdff-207">**MarshalAsAttribute** hazırlama üzerinde hiçbir etkisi diziler yönetilmeyen kod için yönetilen sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-207">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="6fdff-208">Bu yönde dizi boyutu inceleme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-208">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="6fdff-209">Yönetilen bir dizinin bir alt sıralamakta yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-209">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="6fdff-210">Birlikte çalışma Sıralayıcı kullanan **CoTaskMemAlloc** ve **CoTaskMemFree** ayırmak ve bellek almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6fdff-210">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="6fdff-211">Yönetilmeyen kodu tarafından gerçekleştirilen bellek ayırma de bu yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-211">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a><span data-ttu-id="6fdff-212">COM dizileri geçirme</span><span class="sxs-lookup"><span data-stu-id="6fdff-212">Passing Arrays to COM</span></span>  
 <span data-ttu-id="6fdff-213">Tüm yönetilen dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-213">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="6fdff-214">Yönetilen türü ve uygulanan öznitelikleri bağlı olarak, dizi güvenli bir dizi veya bir C tarzı dizisi aşağıdaki tabloda gösterildiği gibi erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-214">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="6fdff-215">Yönetilen dizi türü</span><span class="sxs-lookup"><span data-stu-id="6fdff-215">Managed array type</span></span>|<span data-ttu-id="6fdff-216">Olarak dışarı aktarıldı</span><span class="sxs-lookup"><span data-stu-id="6fdff-216">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="6fdff-217">**ELEMENT_TYPE_SZARRAY** **\<** *türü* **>**</span><span class="sxs-lookup"><span data-stu-id="6fdff-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="6fdff-218"><xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *türü* **)**</span><span class="sxs-lookup"><span data-stu-id="6fdff-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="6fdff-219">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="6fdff-219">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="6fdff-220">Türü imzada sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-220">Type is provided in the signature.</span></span> <span data-ttu-id="6fdff-221">RANK her zaman 1, alt sınır her zaman 0.</span><span class="sxs-lookup"><span data-stu-id="6fdff-221">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="6fdff-222">Boyut her zaman çalışma zamanında denir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="6fdff-223">**ELEMENT_TYPE_ARRAY** **\<** *türü* **>** **\<** *derece* **>**[**\<** *sınırları* **>**]</span><span class="sxs-lookup"><span data-stu-id="6fdff-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="6fdff-224">**UnmanagedType.SafeArray (** *türü* **)**</span><span class="sxs-lookup"><span data-stu-id="6fdff-224">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="6fdff-225">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="6fdff-225">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="6fdff-226">Türü, sıralama, sınırların imzada sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6fdff-226">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="6fdff-227">Boyut her zaman çalışma zamanında denir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-227">Size is always known at run time.</span></span>|  
|<span data-ttu-id="6fdff-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="6fdff-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="6fdff-229">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="6fdff-229">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="6fdff-230">**UnmanagedType.SafeArray (** *türü* **)**</span><span class="sxs-lookup"><span data-stu-id="6fdff-230">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="6fdff-231">Türü, derece, sınırları ve boyutu her zaman çalışma zamanında bilinir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-231">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="6fdff-232">OLE Otomasyonu'ndaki LPSTR veya LPWSTR içeren yapılarını diziler için ilgili bir sınırlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-232">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="6fdff-233">Bu nedenle, **dize** alanları olarak sıralanması zorunda **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-233">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="6fdff-234">Aksi halde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6fdff-234">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="6fdff-235">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="6fdff-235">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="6fdff-236">İçeren bir yöntemi, bir **ELEMENT_TYPE_SZARRAY** parametre (tek boyutlu dizi) bir .NET derleme için bir tür kitaplığı aktarılan, dizi parametresi dönüştürülür bir **SAFEARRAY** belirli bir türde.</span><span class="sxs-lookup"><span data-stu-id="6fdff-236">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="6fdff-237">Dizi öğesi türleri için aynı dönüştürme kurallarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6fdff-237">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="6fdff-238">Yönetilen dizinin içeriğini yönetilen belleğe otomatik olarak kopyalandığı **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-238">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="6fdff-239">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-239">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-240">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-240">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="6fdff-241">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-241">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="6fdff-242">Güvenli diziler derecesini her zaman 1 ve alt sınır her zaman 0.</span><span class="sxs-lookup"><span data-stu-id="6fdff-242">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="6fdff-243">Boyutu çalışma zamanında geçirilen yönetilen dizi boyutu tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-243">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="6fdff-244">Diziye ayrıca bir C tarzı dizisi olarak kullanarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6fdff-244">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="6fdff-245">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-245">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-246">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-246">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="6fdff-247">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-247">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="6fdff-248">Sıralayıcı dizi hazırlamak için gereken uzunluğu bilgileri olsa da, dizi uzunluğu genellikle Aranan uzunluğu iletmek için ayrı bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-248">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="6fdff-249">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="6fdff-249">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="6fdff-250">İçeren bir yöntemi, bir **ELEMENT_TYPE_ARRAY** parametresi için bir tür kitaplığı .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **SAFEARRAY** belirli bir türde.</span><span class="sxs-lookup"><span data-stu-id="6fdff-250">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="6fdff-251">Yönetilen dizinin içeriğini yönetilen belleğe otomatik olarak kopyalandığı **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="6fdff-251">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="6fdff-252">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-253">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-253">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="6fdff-254">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-254">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="6fdff-255">Derece, boyutu ve güvenli diziler sınırları çalışma zamanında yönetilen dizi özelliklerine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-255">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="6fdff-256">Diziye ayrıca bir C tarzı dizisi olarak uygulayarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6fdff-256">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="6fdff-257">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-257">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-258">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-258">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="6fdff-259">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-259">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="6fdff-260">İç içe diziler sıralanamaz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-260">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="6fdff-261">Örneğin, aşağıdaki imzası ile verildiğinde bir hata oluşturur [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="6fdff-261">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-262">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-262">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="6fdff-263">ELEMENT_TYPE_CLASS \<System.Array ></span><span class="sxs-lookup"><span data-stu-id="6fdff-263">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="6fdff-264">İçeren bir yöntemi, bir <xref:System.Array?displayProperty=nameWithType> parametresi için bir tür kitaplığı .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **_Array** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6fdff-264">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="6fdff-265">Yönetilen dizinin içeriğini yalnızca yöntemleri ve özellikleri erişilebilir **_Array** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6fdff-265">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="6fdff-266">**System.Array** olarak sıralanabilir bir **SAFEARRAY** kullanarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6fdff-266">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="6fdff-267">Güvenli bir dizi olarak sıralanmış, dizi öğeleri çeşitleri hazırlanırlar.</span><span class="sxs-lookup"><span data-stu-id="6fdff-267">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="6fdff-268">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6fdff-268">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="6fdff-269">Yönetilen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-269">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="6fdff-270">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fdff-270">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="6fdff-271">Yapıları içindeki diziler</span><span class="sxs-lookup"><span data-stu-id="6fdff-271">Arrays within Structures</span></span>  
 <span data-ttu-id="6fdff-272">Yönetilmeyen yapılar katıştırılmış diziler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-272">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="6fdff-273">Varsayılan olarak, bu katıştırılmış dizi alanları SAFEARRAY hazırlanırlar.</span><span class="sxs-lookup"><span data-stu-id="6fdff-273">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="6fdff-274">Aşağıdaki örnekte, `s1` doğrudan yapısında kendisine ayrılan katıştırılmış bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="6fdff-274">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="6fdff-275">Yönetilmeyen gösterimi</span><span class="sxs-lookup"><span data-stu-id="6fdff-275">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="6fdff-276">Diziler sıralanmış olarak <xref:System.Runtime.InteropServices.UnmanagedType>, ayarlamanızı gerektiren <xref:System.Runtime.InteropServices.MarshalAsAttribute> alan.</span><span class="sxs-lookup"><span data-stu-id="6fdff-276">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="6fdff-277">Boyut yalnızca bir sabit değer olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-277">The size can be set only as a constant.</span></span> <span data-ttu-id="6fdff-278">Aşağıdaki kod karşılık gelen yönetilen tanımını gösterir `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="6fdff-278">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6fdff-279">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fdff-279">See Also</span></span>  
 [<span data-ttu-id="6fdff-280">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="6fdff-280">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="6fdff-281">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="6fdff-281">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="6fdff-282">[Tek yönlü öznitelikleri](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6fdff-282">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="6fdff-283">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="6fdff-283">Copying and Pinning</span></span>](copying-and-pinning.md)
