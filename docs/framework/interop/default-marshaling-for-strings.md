---
title: Dizeler için Varsayılan Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47543056eaa538b008db3332dda776c0f300108d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078479"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="19199-102">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="19199-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="19199-103">Hem <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflar benzer hazırlama davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="19199-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="19199-104">Dizeleri bir COM stili olarak sıralanmış `BSTR` türü veya null ile sonlandırılmış bir dize (boş bir karakter ile sona eren bir karakter dizisi) olarak.</span><span class="sxs-lookup"><span data-stu-id="19199-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="19199-105">Unicode (Windows sistemlerinde varsayılan) veya ANSI olarak dize içindeki karakterlerin sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="19199-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="19199-106">Bu konu, dize türlerini hazırlama hakkında aşağıdaki bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="19199-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="19199-107">Arabirimlerde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="19199-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="19199-108">Dizeleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="19199-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="19199-109">Yapıları, kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="19199-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="19199-110">Sabit uzunluklu dize arabelleği</span><span class="sxs-lookup"><span data-stu-id="19199-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="19199-111">Arabirimlerde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="19199-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="19199-112">Aşağıdaki tablo, yönetilmeyen kodu bir metot bağımsız değişkeni olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19199-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="19199-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için COM arabirimlerine dizelerini sıralama.</span><span class="sxs-lookup"><span data-stu-id="19199-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="19199-114">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="19199-114">Enumeration type</span></span>|<span data-ttu-id="19199-115">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="19199-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="19199-116">`UnmanagedType.BStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="19199-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="19199-117">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="19199-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="19199-118">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="19199-119">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="19199-120">Bu tablo, dizeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19199-120">This table applies to strings.</span></span> <span data-ttu-id="19199-121">Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="19199-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="19199-122">Aşağıdaki örnek, dizeleri bildirilen gösterir `IStringWorker` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="19199-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);
```

<span data-ttu-id="19199-123">Aşağıdaki örnek, bir tür kitaplığında tanımlanan karşılık gelen arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="19199-123">The following example shows the corresponding interface described in a type library.</span></span>

```
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);
```

<a name="cpcondefaultmarshalingforstringsanchor5"></a>

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="19199-124">Dizeleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="19199-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="19199-125">Platform çağırma kopyaları dize bağımsız değişkenleri, .NET Framework biçimden (Unicode) platform yönetilmeyen biçimine dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="19199-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="19199-126">Dizeleri sabittir ve yönetilmeyen belleğin geri çağrısı döndürüldüğünde yönetilen bellek kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="19199-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="19199-127">Aşağıdaki tabloda bir yöntemi bağımsız değişken bir platform çağırma olarak çağrı sıralandığı zaman dizeler için sıralama seçenekleri listeler.</span><span class="sxs-lookup"><span data-stu-id="19199-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="19199-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi dizelerini sıralama için değerler.</span><span class="sxs-lookup"><span data-stu-id="19199-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="19199-129">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="19199-129">Enumeration type</span></span>|<span data-ttu-id="19199-130">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="19199-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="19199-131">COM Stili `BSTR` önekli bir uzunluk ve ANSI karakterler.</span><span class="sxs-lookup"><span data-stu-id="19199-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="19199-132">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="19199-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="19199-133">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="19199-134">Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="19199-135">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="19199-136">COM Stili `BSTR` önekli bir uzunluk ve platforma bağımlı karakter.</span><span class="sxs-lookup"><span data-stu-id="19199-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="19199-137">Bir dizede değiştirilecek Visual Basic .NET sağlayan bir değer kod yönetilmeyen ve yönetilen kodda sonuçları yansıtılmasını.</span><span class="sxs-lookup"><span data-stu-id="19199-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="19199-138">Bu değer, yalnızca platform çağırma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19199-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="19199-139">Visual Basic için varsayılan değer budur `ByVal` dizeleri.</span><span class="sxs-lookup"><span data-stu-id="19199-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="19199-140">Bu tablo, dizeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19199-140">This table applies to strings.</span></span> <span data-ttu-id="19199-141">Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `LPStr`, `LPTStr`, ve `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="19199-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="19199-142">Aşağıdaki tür tanımı doğru kullanımını gösterir `MarshalAsAttribute` çağrıları için platform çağırma.</span><span class="sxs-lookup"><span data-stu-id="19199-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```

```csharp
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a><span data-ttu-id="19199-143">Yapıları, kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="19199-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="19199-144">Dizeleri yapıları geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekler yapılarda geçersiz.</span><span class="sxs-lookup"><span data-stu-id="19199-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="19199-145">Aşağıdaki tabloda, türü, bir alan olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19199-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="19199-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için bir alan için dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="19199-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="19199-147">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="19199-147">Enumeration type</span></span>|<span data-ttu-id="19199-148">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="19199-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="19199-149">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="19199-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="19199-150">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="19199-151">Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="19199-152">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19199-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="19199-153">Karakter sabit uzunluklu dizi; dizi türü içeren yapı karakter kümesi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="19199-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="19199-154">`ByValTStr` Türü satır içi, bir yapı içinde görünen sabit uzunluklu karakteri diziler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19199-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="19199-155">Diğer türleri dizelerine içeren yapıları içindeki dize başvuruları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19199-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="19199-156">`CharSet` Bağımsız değişkeni <xref:System.Runtime.InteropServices.StructLayoutAttribute> içeren yapı için uygulanan bir öznitelik yapılardaki dize karakter biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="19199-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="19199-157">Aşağıdaki örnek yapılardaki dize başvurular ve satır içi dizeleri yanı sıra ANSI, Unicode ve platforma bağımlı karakter içerir.</span><span class="sxs-lookup"><span data-stu-id="19199-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="19199-158">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="19199-158">Type Library Representation</span></span>  
  
```
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 <span data-ttu-id="19199-159">Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapısını tanımlayan öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19199-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="19199-160">Sabit uzunluklu dize arabelleği</span><span class="sxs-lookup"><span data-stu-id="19199-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="19199-161">Bazı durumlarda, sabit uzunluklu karakteri arabellek yönetilebilmesini yönetilmeyen koda geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="19199-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="19199-162">Çağrılan geçirilen arabellek içeriği değiştirilemez çünkü yalnızca bir dizeye geçiliyor bu durumda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="19199-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="19199-163">Dize başvuruya göre geçirilse bile, verilen boyuta arabellek başlatmak için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="19199-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="19199-164">Çözüm geçirmektir bir <xref:System.Text.StringBuilder> bağımsız değişkeni bir dize yerine arabellek.</span><span class="sxs-lookup"><span data-stu-id="19199-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="19199-165">A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="19199-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="19199-166">Sabit uzunluk için de yeniden başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="19199-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="19199-167">Örneğin, başlatma, bir `StringBuilder` kapasitesi arabelleğe `N`, Sıralayıcı bir arabellek boyutunu sağlar (`N`+ 1) karakter.</span><span class="sxs-lookup"><span data-stu-id="19199-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="19199-168">Yönetilmeyen dize bir null Sonlandırıcı çalışırken sahip olgu + 1 hesaplar `StringBuilder` desteklemez.</span><span class="sxs-lookup"><span data-stu-id="19199-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="19199-169">Örneğin, Microsoft Windows API `GetWindowText` (Windows.h içinde tanımlanmıştır) yönetilebilmesini yönetilmeyen koda geçirilmelidir sabit uzunluklu karakteri arabellek işlevdir.</span><span class="sxs-lookup"><span data-stu-id="19199-169">For example, the Microsoft Windows API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="19199-170">`LpString` işaret boyutu arayana ayrılan arabelleğe `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="19199-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="19199-171">Çağıranın arabellek ayırmak ve ayarlamak için beklenen `nMaxCount` bağımsız değişkeni için ayrılan arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="19199-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="19199-172">Aşağıdaki kodda gösterildiği `GetWindowText` işlevi bildiriminde Windows.h içinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="19199-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="19199-173">A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="19199-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="19199-174">Aşağıdaki kod örneğinde nasıl `StringBuilder` sabit uzunluk için başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="19199-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="19199-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19199-175">See also</span></span>

- [<span data-ttu-id="19199-176">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="19199-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="19199-177">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="19199-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="19199-178">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="19199-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="19199-179">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="19199-179">Copying and Pinning</span></span>](copying-and-pinning.md)
