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
ms.openlocfilehash: 49f2d871a42db484e20f0bfc35634a0e8b959c2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123544"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="7fa3d-102">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7fa3d-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="7fa3d-103"><xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflarının her ikisi de benzer sıralama davranışına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="7fa3d-104">Dizeler bir COM stili `BSTR` türü olarak veya null ile sonlandırılmış bir dize (null karakterle biten bir karakter dizisi) olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="7fa3d-105">Dize içindeki karakterler Unicode olarak sıralanabilir (Windows sistemlerinde varsayılan olarak) veya ANSI.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="7fa3d-106">Arabirimlerde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="7fa3d-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="7fa3d-107">Aşağıdaki tabloda, yönetilmeyen koda bir yöntem bağımsız değişkeni olarak sıralandığınızda dize veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="7fa3d-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizelerin COM arabirimlerine sıralaması için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="7fa3d-109">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="7fa3d-109">Enumeration type</span></span>|<span data-ttu-id="7fa3d-110">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="7fa3d-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="7fa3d-111">`UnmanagedType.BStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="7fa3d-112">Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="7fa3d-113">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="7fa3d-114">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="7fa3d-115">Bu tablo <xref:System.String>için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="7fa3d-116"><xref:System.Text.StringBuilder>için izin verilen tek seçenek `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="7fa3d-117">Aşağıdaki örnek, `IStringWorker` arabiriminde belirtilen dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

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

<span data-ttu-id="7fa3d-118">Aşağıdaki örnekte, bir tür kitaplığında açıklanan karşılık gelen arabirim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-118">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="7fa3d-119">Platform çağırma içinde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="7fa3d-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="7fa3d-120">Platform çağrısı, .NET Framework biçiminden (Unicode) Platform yönetilmeyen biçimine dönüştürerek dize bağımsız değişkenlerini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="7fa3d-121">Dizeler sabittir ve çağrı geri döndüğünde yönetilen belleğe yönetilmeyen bellekten geri kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="7fa3d-122">Aşağıdaki tabloda, bir platform çağırma çağrısının Yöntem bağımsız değişkeni olarak sıralandığınızda dizeler için sıralama seçenekleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="7fa3d-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizeleri sıralamak için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="7fa3d-124">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="7fa3d-124">Enumeration type</span></span>|<span data-ttu-id="7fa3d-125">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="7fa3d-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="7fa3d-126">Ön ek uzunluğu ve ANSI karakterleri olan bir COM stili `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="7fa3d-127">Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="7fa3d-128">`UnmanagedType.LPStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="7fa3d-129">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="7fa3d-130">Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="7fa3d-131">UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-131">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="7fa3d-132">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-132">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="7fa3d-133">Ön ek uzunluğu ve platforma bağlı karakterlerle bir COM stili `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-133">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="7fa3d-134">Visual Basic .NET 'in yönetilmeyen koddaki bir dizeyi değiştirmesini ve sonuçların yönetilen koda yansıtılmasını sağlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-134">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="7fa3d-135">Bu değer yalnızca platform çağırma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-135">This value is supported only for platform invoke.</span></span> <span data-ttu-id="7fa3d-136">Bu, `ByVal` dizeleri için Visual Basic varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-136">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="7fa3d-137">Bu tablo <xref:System.String>için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-137">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="7fa3d-138"><xref:System.Text.StringBuilder>için izin verilen tek seçenek `LPStr`, `LPTStr`ve `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-138">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="7fa3d-139">Aşağıdaki tür tanımı, platform çağırma çağrıları için `MarshalAsAttribute` doğru kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-139">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

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
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
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
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="7fa3d-140">Yapılarda kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="7fa3d-140">Strings Used in Structures</span></span>

<span data-ttu-id="7fa3d-141">Dizeler yapıların geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekleri yapılarda geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-141">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="7fa3d-142">Aşağıdaki tabloda, tür bir alan olarak sıralandığınızda <xref:System.String> veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-142">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="7fa3d-143"><xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, bir alana dizeleri sıralamak için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-143">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="7fa3d-144">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="7fa3d-144">Enumeration type</span></span>|<span data-ttu-id="7fa3d-145">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="7fa3d-145">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="7fa3d-146">Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-146">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="7fa3d-147">`UnmanagedType.LPStr` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-147">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="7fa3d-148">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-148">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="7fa3d-149">Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-149">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="7fa3d-150">UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-150">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="7fa3d-151">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-151">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="7fa3d-152">Sabit uzunluklu karakter dizisi; dizinin türü, kapsayan yapının karakter kümesi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-152">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="7fa3d-153">`ByValTStr` türü, bir yapı içinde görünen satır içi, sabit uzunlukta karakter dizileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-153">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="7fa3d-154">Diğer türler, dizeler için işaretçiler içeren yapılar içinde yer alan dize başvuruları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-154">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="7fa3d-155">İçerilen yapıya uygulanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> `CharSet` bağımsız değişkeni, yapılardaki dizelerin karakter biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-155">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="7fa3d-156">Aşağıdaki örnek yapılar dize başvurularını ve satır içi dizeleri, ayrıca ANSI, Unicode ve platforma bağımlı karakterleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-156">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="7fa3d-157">Bir tür kitaplığındaki bu yapıların temsili aşağıdaki C++ kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-157">The representation of these structures in a type library is shown in the following C++ code:</span></span>

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

<span data-ttu-id="7fa3d-158">Aşağıdaki örnek, farklı biçimlerde aynı yapıyı tanımlamak için <xref:System.Runtime.InteropServices.MarshalAsAttribute> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-158">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="7fa3d-159">Sabit uzunluklu dize arabellekleri</span><span class="sxs-lookup"><span data-stu-id="7fa3d-159">Fixed-Length String Buffers</span></span>

<span data-ttu-id="7fa3d-160">Bazı durumlarda, sabit uzunluklu bir karakter arabelleğinin, kullanılacak yönetilmeyen koda geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-160">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="7fa3d-161">Çağıran, geçilen arabelleğin içeriğini değiştiremediğinden, bu durumda yalnızca bir dize geçirilmesi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-161">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="7fa3d-162">Dize başvuruya göre geçirilse bile, arabelleği verilen boyuta başlatmanın bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-162">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="7fa3d-163">Çözüm, bir <xref:System.Text.StringBuilder> arabelleğini <xref:System.String>yerine bağımsız değişken olarak geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-163">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="7fa3d-164">`StringBuilder`, `StringBuilder`kapasitesini aşmadığı belirtilen aranan tarafından bir başvuru yapılabilir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-164">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="7fa3d-165">Ayrıca, sabit bir uzunluğa de başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-165">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="7fa3d-166">Örneğin, bir `N`kapasitesine `StringBuilder` arabelleği başlattığınızda Sıralayıcı, boyut (`N`+ 1) karakter arabelleği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-166">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="7fa3d-167">Yönetilmeyen dizenin `StringBuilder` null sonlandırıcısına sahip olduğu için + 1 hesapları.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-167">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="7fa3d-168">Örneğin, Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API işlevi ( *Winuser. h*içinde tanımlanan), çağıranın, işlevin pencerenin metnini yazdığı sabit uzunlukta bir karakter arabelleği geçmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-168">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="7fa3d-169">`LpString`, çağıran bir boyut `nMaxCount`arabelleğini işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-169">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="7fa3d-170">Çağıranın arabelleği ayırması ve `nMaxCount` bağımsız değişkenini ayrılan arabelleğin boyutuna ayarlaması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-170">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="7fa3d-171">Aşağıdaki örnek, `GetWindowText` işlev bildirimini *Winuser. h*içinde tanımlanan şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-171">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="7fa3d-172">`StringBuilder`, `StringBuilder`kapasitesini aşmadığı belirtilen aranan tarafından bir başvuru yapılabilir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-172">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="7fa3d-173">Aşağıdaki kod örneği `StringBuilder` sabit bir uzunluğa nasıl başlatılabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-173">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
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
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="7fa3d-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-174">See also</span></span>

- [<span data-ttu-id="7fa3d-175">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="7fa3d-175">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="7fa3d-176">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7fa3d-176">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="7fa3d-177">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="7fa3d-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="7fa3d-178">[Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7fa3d-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="7fa3d-179">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="7fa3d-179">Copying and Pinning</span></span>](copying-and-pinning.md)
