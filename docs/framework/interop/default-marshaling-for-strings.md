---
title: Dizeler için Varsayılan Hazırlama
description: .NET 'teki arabirimlerde, platform Invoke, yapılar & sabit uzunluklu dize arabelleklerinde bulunan dizeler için varsayılan sıralama davranışını gözden geçirin.
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
ms.openlocfilehash: 81df2dcc132c8ce057fa3e0e7d0ad04832f7a48b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555061"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="94cdb-103">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="94cdb-103">Default Marshaling for Strings</span></span>

<span data-ttu-id="94cdb-104">Hem <xref:System.String?displayProperty=nameWithType> hem de <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflarının benzer sıralama davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="94cdb-104">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="94cdb-105">Dizeler bir COM stili `BSTR` türü olarak veya null ile sonlandırılmış bir dize (null karakterle biten bir karakter dizisi) olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="94cdb-105">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="94cdb-106">Dize içindeki karakterler Unicode olarak sıralanabilir (Windows sistemlerinde varsayılan olarak) veya ANSI.</span><span class="sxs-lookup"><span data-stu-id="94cdb-106">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="94cdb-107">Arabirimlerde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="94cdb-107">Strings Used in Interfaces</span></span>

<span data-ttu-id="94cdb-108">Aşağıdaki tabloda, yönetilmeyen koda bir yöntem bağımsız değişkeni olarak sıralandığınızda dize veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-108">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="94cdb-109"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> dizelerin com arabirimlerine sıralaması için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="94cdb-109">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="94cdb-110">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="94cdb-110">Enumeration type</span></span>|<span data-ttu-id="94cdb-111">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="94cdb-111">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="94cdb-112">`UnmanagedType.BStr` varsayılanını</span><span class="sxs-lookup"><span data-stu-id="94cdb-112">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="94cdb-113">`BSTR`Ön ek uzunluğu ve Unicode karakterleri olan BIR com stili.</span><span class="sxs-lookup"><span data-stu-id="94cdb-113">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="94cdb-114">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-114">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="94cdb-115">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-115">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="94cdb-116">Bu tablo için geçerlidir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="94cdb-116">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="94cdb-117">İçin <xref:System.Text.StringBuilder> , izin verilen tek seçenekler ve ' dir `UnmanagedType.LPStr` `UnmanagedType.LPWStr` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-117">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="94cdb-118">Aşağıdaki örnek, arabiriminde belirtilen dizeleri gösterir `IStringWorker` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-118">The following example shows strings declared in the `IStringWorker` interface.</span></span>

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

<span data-ttu-id="94cdb-119">Aşağıdaki örnekte, bir tür kitaplığında açıklanan karşılık gelen arabirim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-119">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="94cdb-120">Platform çağırma içinde kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="94cdb-120">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="94cdb-121">Platform çağrısı, .NET Framework biçiminden (Unicode) Platform yönetilmeyen biçimine dönüştürerek dize bağımsız değişkenlerini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="94cdb-121">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="94cdb-122">Dizeler sabittir ve çağrı geri döndüğünde yönetilen belleğe yönetilmeyen bellekten geri kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="94cdb-122">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="94cdb-123">Aşağıdaki tabloda, bir platform çağırma çağrısının Yöntem bağımsız değişkeni olarak sıralandığınızda dizeler için sıralama seçenekleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-123">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="94cdb-124"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> dizeleri sıralamak için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="94cdb-124">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="94cdb-125">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="94cdb-125">Enumeration type</span></span>|<span data-ttu-id="94cdb-126">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="94cdb-126">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="94cdb-127">`BSTR`Ön ek uzunluğu ve ANSI karakterleri olan BIR com stili.</span><span class="sxs-lookup"><span data-stu-id="94cdb-127">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="94cdb-128">`BSTR`Ön ek uzunluğu ve Unicode karakterleri olan BIR com stili.</span><span class="sxs-lookup"><span data-stu-id="94cdb-128">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="94cdb-129">`UnmanagedType.LPStr` varsayılanını</span><span class="sxs-lookup"><span data-stu-id="94cdb-129">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="94cdb-130">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-130">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="94cdb-131">Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-131">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="94cdb-132">UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-132">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="94cdb-133">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-133">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="94cdb-134">`BSTR`Ön ek uzunluğu ve platforma bağlı karakterlerle BIR com stili.</span><span class="sxs-lookup"><span data-stu-id="94cdb-134">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="94cdb-135">Visual Basic .NET 'in yönetilmeyen koddaki bir dizeyi değiştirmesini ve sonuçların yönetilen koda yansıtılmasını sağlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="94cdb-135">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="94cdb-136">Bu değer yalnızca platform çağırma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-136">This value is supported only for platform invoke.</span></span> <span data-ttu-id="94cdb-137">Bu, dizeler için Visual Basic varsayılan değerdir `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-137">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="94cdb-138">Bu tablo için geçerlidir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="94cdb-138">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="94cdb-139">İçin, <xref:System.Text.StringBuilder> izin verilen tek Seçenekler `LPStr` , ve ' dir `LPTStr` `LPWStr` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-139">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="94cdb-140">Aşağıdaki tür tanımı, `MarshalAsAttribute` Platform çağırma çağrılarının doğru kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-140">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

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

## <a name="strings-used-in-structures"></a><span data-ttu-id="94cdb-141">Yapılarda kullanılan dizeler</span><span class="sxs-lookup"><span data-stu-id="94cdb-141">Strings Used in Structures</span></span>

<span data-ttu-id="94cdb-142">Dizeler yapıların geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> yapılar içinde arabellekler geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-142">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="94cdb-143">Aşağıdaki tabloda, <xref:System.String> tür bir alan olarak sıralandığınızda veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-143">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="94cdb-144"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği <xref:System.Runtime.InteropServices.UnmanagedType> bir alana dizeleri sıralamak için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="94cdb-144">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="94cdb-145">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="94cdb-145">Enumeration type</span></span>|<span data-ttu-id="94cdb-146">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="94cdb-146">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="94cdb-147">`BSTR`Ön ek uzunluğu ve Unicode karakterleri olan BIR com stili.</span><span class="sxs-lookup"><span data-stu-id="94cdb-147">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="94cdb-148">`UnmanagedType.LPStr` varsayılanını</span><span class="sxs-lookup"><span data-stu-id="94cdb-148">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="94cdb-149">ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-149">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="94cdb-150">Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-150">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="94cdb-151">UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-151">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="94cdb-152">Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94cdb-152">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="94cdb-153">Sabit uzunluklu karakter dizisi; dizinin türü, kapsayan yapının karakter kümesi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="94cdb-154">`ByValTStr`Tür, bir yapı içinde görünen satır içi, sabit uzunlukta karakter dizileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94cdb-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="94cdb-155">Diğer türler, dizeler için işaretçiler içeren yapılar içinde yer alan dize başvuruları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="94cdb-156">`CharSet`İçeren yapısına uygulanan öğesinin bağımsız değişkeni, <xref:System.Runtime.InteropServices.StructLayoutAttribute> yapılardaki dizelerin karakter biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="94cdb-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="94cdb-157">Aşağıdaki örnek yapılar dize başvurularını ve satır içi dizeleri, ayrıca ANSI, Unicode ve platforma bağımlı karakterleri içerir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="94cdb-158">Bir tür kitaplığındaki bu yapıların temsili aşağıdaki C++ kodunda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="94cdb-158">The representation of these structures in a type library is shown in the following C++ code:</span></span>

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

<span data-ttu-id="94cdb-159">Aşağıdaki örnek, <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapıyı tanımlamak için ' nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-159">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="94cdb-160">Sabit uzunluklu dize arabellekleri</span><span class="sxs-lookup"><span data-stu-id="94cdb-160">Fixed-Length String Buffers</span></span>

<span data-ttu-id="94cdb-161">Bazı durumlarda, sabit uzunluklu bir karakter arabelleğinin, kullanılacak yönetilmeyen koda geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="94cdb-162">Çağıran, geçilen arabelleğin içeriğini değiştiremediğinden, bu durumda yalnızca bir dize geçirilmesi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="94cdb-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="94cdb-163">Dize başvuruya göre geçirilse bile, arabelleği verilen boyuta başlatmanın bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="94cdb-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="94cdb-164">Çözüm, <xref:System.Text.StringBuilder> bir arabelleği bir yerine bağımsız değişken olarak geçirmektir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="94cdb-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="94cdb-165">Bir öğesine başvuru `StringBuilder` yapılabilir ve bu, öğesinin kapasitesini aşmadığı belirtilen aranan tarafından değiştirilebilir `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="94cdb-166">Ayrıca, sabit bir uzunluğa de başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="94cdb-167">Örneğin, bir kapasiteye bir arabellek başladıysanız `StringBuilder` `N` , Sıralayıcı boyut ( `N` + 1) karakter arabelleği sağlar.</span><span class="sxs-lookup"><span data-stu-id="94cdb-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="94cdb-168">Yönetilmeyen dizenin null sonlandırıcısına sahip olmadığı için + 1 hesapları `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="94cdb-169">Örneğin, Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API işlevi ( *Winuser. h*içinde tanımlanmıştır) çağıranın, işlevin pencerenin metnini yazdığı sabit uzunlukta bir karakter arabelleği geçmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-169">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="94cdb-170">`LpString` çağıran, ayrılmış bir arabellek boyutunu gösterir `nMaxCount` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="94cdb-171">Çağıranın arabelleği ayırması ve `nMaxCount` bağımsız değişkeni ayrılan arabelleğin boyutuna ayarlaması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="94cdb-172">Aşağıdaki örnek, `GetWindowText` işlev bildirimini *Winuser. h*içinde tanımlanan şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-172">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="94cdb-173">Bir öğesine başvuru `StringBuilder` yapılabilir ve bu, öğesinin kapasitesini aşmadığı belirtilen aranan tarafından değiştirilebilir `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="94cdb-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="94cdb-174">Aşağıdaki kod örneği, nasıl `StringBuilder` sabit bir uzunluğa başlatılabileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="94cdb-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="94cdb-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94cdb-175">See also</span></span>

- [<span data-ttu-id="94cdb-176">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="94cdb-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="94cdb-177">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="94cdb-177">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="94cdb-178">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="94cdb-178">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="94cdb-179">[Yönlü öznitelikler](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94cdb-179">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="94cdb-180">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="94cdb-180">Copying and Pinning</span></span>](copying-and-pinning.md)
