---
title: Dizeler için Varsayılan Hazırlama
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4433f05a76d389f6dda5afcfe898d942c4e7d05f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978529"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="667ce-102">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="667ce-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="667ce-103">Hem <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflar benzer hazırlama davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="667ce-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="667ce-104">Dizeleri bir COM stili olarak sıralanmış `BSTR` türü veya null ile sonlandırılmış bir dize (boş bir karakter ile sona eren bir karakter dizisi) olarak.</span><span class="sxs-lookup"><span data-stu-id="667ce-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="667ce-105">Unicode (Windows sistemlerinde varsayılan) veya ANSI olarak dize içindeki karakterlerin sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="667ce-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="667ce-106">Arabirimlerde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="667ce-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="667ce-107">Aşağıdaki tablo, yönetilmeyen kodu bir metot bağımsız değişkeni olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="667ce-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="667ce-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için COM arabirimlerine dizelerini sıralama.</span><span class="sxs-lookup"><span data-stu-id="667ce-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="667ce-109">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="667ce-109">Enumeration type</span></span>|<span data-ttu-id="667ce-110">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="667ce-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="667ce-111">`UnmanagedType.BStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="667ce-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="667ce-112">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="667ce-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="667ce-113">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="667ce-114">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="667ce-115">Bu tabloda uygulandığı <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="667ce-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="667ce-116">İçin <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="667ce-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="667ce-117">Aşağıdaki örnek, dizeleri bildirilen gösterir `IStringWorker` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="667ce-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="667ce-118">Aşağıdaki örnek, bir tür kitaplığında tanımlanan karşılık gelen arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="667ce-118">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="667ce-119">Dizeleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="667ce-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="667ce-120">Platform çağırma kopyaları dize bağımsız değişkenleri, .NET Framework biçimden (Unicode) platform yönetilmeyen biçimine dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="667ce-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="667ce-121">Dizeleri sabittir ve yönetilmeyen belleğin geri çağrısı döndürüldüğünde yönetilen bellek kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="667ce-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="667ce-122">Aşağıdaki tabloda bir yöntemi bağımsız değişken bir platform çağırma olarak çağrı sıralandığı zaman dizeler için sıralama seçenekleri listeler.</span><span class="sxs-lookup"><span data-stu-id="667ce-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="667ce-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi dizelerini sıralama için değerler.</span><span class="sxs-lookup"><span data-stu-id="667ce-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="667ce-124">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="667ce-124">Enumeration type</span></span>|<span data-ttu-id="667ce-125">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="667ce-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="667ce-126">COM Stili `BSTR` önekli bir uzunluk ve ANSI karakterler.</span><span class="sxs-lookup"><span data-stu-id="667ce-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="667ce-127">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="667ce-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="667ce-128">`UnmanagedType.LPStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="667ce-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="667ce-129">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="667ce-130">Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="667ce-131">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-131">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="667ce-132">COM Stili `BSTR` önekli bir uzunluk ve platforma bağımlı karakter.</span><span class="sxs-lookup"><span data-stu-id="667ce-132">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="667ce-133">Bir dizede değiştirilecek Visual Basic .NET sağlayan bir değer kod yönetilmeyen ve yönetilen kodda sonuçları yansıtılmasını.</span><span class="sxs-lookup"><span data-stu-id="667ce-133">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="667ce-134">Bu değer, yalnızca platform çağırma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="667ce-134">This value is supported only for platform invoke.</span></span> <span data-ttu-id="667ce-135">Visual Basic için varsayılan değer budur `ByVal` dizeleri.</span><span class="sxs-lookup"><span data-stu-id="667ce-135">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="667ce-136">Bu tabloda uygulandığı <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="667ce-136">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="667ce-137">İçin <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `LPStr`, `LPTStr`, ve `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="667ce-137">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="667ce-138">Aşağıdaki tür tanımı doğru kullanımını gösterir `MarshalAsAttribute` çağrıları için platform çağırma.</span><span class="sxs-lookup"><span data-stu-id="667ce-138">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" _
        (<MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="667ce-139">Yapıları, kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="667ce-139">Strings Used in Structures</span></span>

<span data-ttu-id="667ce-140">Dizeleri yapıları geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekler yapılarda geçersiz.</span><span class="sxs-lookup"><span data-stu-id="667ce-140">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="667ce-141">Sıralama seçenekleri aşağıdaki tabloda gösterilmektedir <xref:System.String> veri türü, bir alan olarak sıralandığı zaman türü.</span><span class="sxs-lookup"><span data-stu-id="667ce-141">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="667ce-142"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için bir alan için dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="667ce-142">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="667ce-143">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="667ce-143">Enumeration type</span></span>|<span data-ttu-id="667ce-144">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="667ce-144">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="667ce-145">COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="667ce-145">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="667ce-146">`UnmanagedType.LPStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="667ce-146">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="667ce-147">Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-147">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="667ce-148">Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-148">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="667ce-149">Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="667ce-149">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="667ce-150">Karakter sabit uzunluklu dizi; dizi türü içeren yapı karakter kümesi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="667ce-150">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="667ce-151">`ByValTStr` Türü satır içi, bir yapı içinde görünen sabit uzunluklu karakteri diziler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="667ce-151">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="667ce-152">Diğer türleri dizelerine içeren yapıları içindeki dize başvuruları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="667ce-152">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="667ce-153">`CharSet` Bağımsız değişkeni <xref:System.Runtime.InteropServices.StructLayoutAttribute> içeren uygulanan yapısı yapılardaki dize karakter biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="667ce-153">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="667ce-154">Aşağıdaki örnek yapılardaki dize başvurular ve satır içi dizeleri yanı sıra ANSI, Unicode ve platforma bağımlı karakter içerir.</span><span class="sxs-lookup"><span data-stu-id="667ce-154">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="667ce-155">Bu yapılar, tür kitaplığındaki gösterimini aşağıda gösterilir C++ kod:</span><span class="sxs-lookup"><span data-stu-id="667ce-155">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="667ce-156">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapısını tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="667ce-156">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="667ce-157">Sabit uzunluklu dize arabelleği</span><span class="sxs-lookup"><span data-stu-id="667ce-157">Fixed-Length String Buffers</span></span>

<span data-ttu-id="667ce-158">Bazı durumlarda, sabit uzunluklu karakteri arabellek yönetilebilmesini yönetilmeyen koda geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="667ce-158">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="667ce-159">Çağrılan geçirilen arabellek içeriği değiştirilemez çünkü yalnızca bir dizeye geçiliyor bu durumda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="667ce-159">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="667ce-160">Dize başvuruya göre geçirilse bile, verilen boyuta arabellek başlatmak için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="667ce-160">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="667ce-161">Çözüm geçirmektir bir <xref:System.Text.StringBuilder> arabellek yerine bağımsız değişken olarak bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="667ce-161">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="667ce-162">A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="667ce-162">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="667ce-163">Sabit uzunluk için de yeniden başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="667ce-163">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="667ce-164">Örneğin, başlatma, bir `StringBuilder` kapasitesi arabelleğe `N`, Sıralayıcı bir arabellek boyutunu sağlar (`N`+ 1) karakter.</span><span class="sxs-lookup"><span data-stu-id="667ce-164">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="667ce-165">Yönetilmeyen dize bir null Sonlandırıcı çalışırken sahip olgu + 1 hesaplar `StringBuilder` desteklemez.</span><span class="sxs-lookup"><span data-stu-id="667ce-165">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="667ce-166">Örneğin, Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API işlevi (tanımlanan *Windows.h*) arayan işlev Yazar pencerenin metin sabit uzunluklu karakteri arabellek geçmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="667ce-166">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *Windows.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="667ce-167">`LpString` işaret boyutu arayana ayrılan arabelleğe `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="667ce-167">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="667ce-168">Çağıranın arabellek ayırmak ve ayarlamak için beklenen `nMaxCount` bağımsız değişkeni için ayrılan arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="667ce-168">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="667ce-169">Aşağıdaki örnekte gösterildiği `GetWindowText` işlevi bildiriminde tanımlanan *Windows.h*.</span><span class="sxs-lookup"><span data-stu-id="667ce-169">The following example shows the `GetWindowText` function declaration as defined in *Windows.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="667ce-170">A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="667ce-170">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="667ce-171">Aşağıdaki kod örneğinde nasıl `StringBuilder` sabit uzunluk için başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="667ce-171">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
internal static class WindowsAPI
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="667ce-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="667ce-172">See also</span></span>

- [<span data-ttu-id="667ce-173">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="667ce-173">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="667ce-174">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="667ce-174">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="667ce-175">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="667ce-175">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="667ce-176">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="667ce-176">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="667ce-177">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="667ce-177">Copying and Pinning</span></span>](copying-and-pinning.md)
