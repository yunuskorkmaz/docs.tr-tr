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
# <a name="default-marshaling-for-strings"></a>Dizeler için Varsayılan Hazırlama

<xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflarının her ikisi de benzer sıralama davranışına sahiptir.

Dizeler bir COM stili `BSTR` türü olarak veya null ile sonlandırılmış bir dize (null karakterle biten bir karakter dizisi) olarak sıralanır. Dize içindeki karakterler Unicode olarak sıralanabilir (Windows sistemlerinde varsayılan olarak) veya ANSI.

## <a name="strings-used-in-interfaces"></a>Arabirimlerde kullanılan dizeler

Aşağıdaki tabloda, yönetilmeyen koda bir yöntem bağımsız değişkeni olarak sıralandığınızda dize veri türü için sıralama seçenekleri gösterilmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizelerin COM arabirimlerine sıralaması için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.

|Sabit listesi türü|Yönetilmeyen biçimin açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (varsayılan)|Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.|
|`UnmanagedType.LPStr`|ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPWStr`|Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|

Bu tablo <xref:System.String>için geçerlidir. <xref:System.Text.StringBuilder>için izin verilen tek seçenek `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.

Aşağıdaki örnek, `IStringWorker` arabiriminde belirtilen dizeleri gösterir.

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

Aşağıdaki örnekte, bir tür kitaplığında açıklanan karşılık gelen arabirim gösterilmektedir.

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

## <a name="strings-used-in-platform-invoke"></a>Platform çağırma içinde kullanılan dizeler

Platform çağrısı, .NET Framework biçiminden (Unicode) Platform yönetilmeyen biçimine dönüştürerek dize bağımsız değişkenlerini kopyalar. Dizeler sabittir ve çağrı geri döndüğünde yönetilen belleğe yönetilmeyen bellekten geri kopyalanmaz.

Aşağıdaki tabloda, bir platform çağırma çağrısının Yöntem bağımsız değişkeni olarak sıralandığınızda dizeler için sıralama seçenekleri listelenmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizeleri sıralamak için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.

|Sabit listesi türü|Yönetilmeyen biçimin açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|Ön ek uzunluğu ve ANSI karakterleri olan bir COM stili `BSTR`.|
|`UnmanagedType.BStr`|Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.|
|`UnmanagedType.LPStr` (varsayılan)|ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPTStr`|Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPUTF8Str`|UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPWStr`|Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.TBStr`|Ön ek uzunluğu ve platforma bağlı karakterlerle bir COM stili `BSTR`.|
|`VBByRefStr`|Visual Basic .NET 'in yönetilmeyen koddaki bir dizeyi değiştirmesini ve sonuçların yönetilen koda yansıtılmasını sağlayan bir değer. Bu değer yalnızca platform çağırma için desteklenir. Bu, `ByVal` dizeleri için Visual Basic varsayılan değerdir.|

Bu tablo <xref:System.String>için geçerlidir. <xref:System.Text.StringBuilder>için izin verilen tek seçenek `LPStr`, `LPTStr`ve `LPWStr`.

Aşağıdaki tür tanımı, platform çağırma çağrıları için `MarshalAsAttribute` doğru kullanımını gösterir.

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

## <a name="strings-used-in-structures"></a>Yapılarda kullanılan dizeler

Dizeler yapıların geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekleri yapılarda geçersizdir. Aşağıdaki tabloda, tür bir alan olarak sıralandığınızda <xref:System.String> veri türü için sıralama seçenekleri gösterilmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, bir alana dizeleri sıralamak için birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.

|Sabit listesi türü|Yönetilmeyen biçimin açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|Ön ek uzunluğu ve Unicode karakterlerle bir COM stili `BSTR`.|
|`UnmanagedType.LPStr` (varsayılan)|ANSI karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPTStr`|Platforma bağlı karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPUTF8Str`|UTF-8 kodlu karakterlerin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.LPWStr`|Unicode karakterlerinin null ile sonlandırılmış dizisine yönelik bir işaretçi.|
|`UnmanagedType.ByValTStr`|Sabit uzunluklu karakter dizisi; dizinin türü, kapsayan yapının karakter kümesi tarafından belirlenir.|

`ByValTStr` türü, bir yapı içinde görünen satır içi, sabit uzunlukta karakter dizileri için kullanılır. Diğer türler, dizeler için işaretçiler içeren yapılar içinde yer alan dize başvuruları için geçerlidir.

İçerilen yapıya uygulanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> `CharSet` bağımsız değişkeni, yapılardaki dizelerin karakter biçimini belirler. Aşağıdaki örnek yapılar dize başvurularını ve satır içi dizeleri, ayrıca ANSI, Unicode ve platforma bağımlı karakterleri içerir. Bir tür kitaplığındaki bu yapıların temsili aşağıdaki C++ kodda gösterilmiştir:

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

Aşağıdaki örnek, farklı biçimlerde aynı yapıyı tanımlamak için <xref:System.Runtime.InteropServices.MarshalAsAttribute> nasıl kullanacağınızı gösterir.

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

## <a name="fixed-length-string-buffers"></a>Sabit uzunluklu dize arabellekleri

Bazı durumlarda, sabit uzunluklu bir karakter arabelleğinin, kullanılacak yönetilmeyen koda geçirilmesi gerekir. Çağıran, geçilen arabelleğin içeriğini değiştiremediğinden, bu durumda yalnızca bir dize geçirilmesi çalışmaz. Dize başvuruya göre geçirilse bile, arabelleği verilen boyuta başlatmanın bir yolu yoktur.

Çözüm, bir <xref:System.Text.StringBuilder> arabelleğini <xref:System.String>yerine bağımsız değişken olarak geçirmektir. `StringBuilder`, `StringBuilder`kapasitesini aşmadığı belirtilen aranan tarafından bir başvuru yapılabilir ve değiştirilebilir. Ayrıca, sabit bir uzunluğa de başlatılabilir. Örneğin, bir `N`kapasitesine `StringBuilder` arabelleği başlattığınızda Sıralayıcı, boyut (`N`+ 1) karakter arabelleği sağlar. Yönetilmeyen dizenin `StringBuilder` null sonlandırıcısına sahip olduğu için + 1 hesapları.

Örneğin, Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API işlevi ( *Winuser. h*içinde tanımlanan), çağıranın, işlevin pencerenin metnini yazdığı sabit uzunlukta bir karakter arabelleği geçmesini gerektirir. `LpString`, çağıran bir boyut `nMaxCount`arabelleğini işaret eder. Çağıranın arabelleği ayırması ve `nMaxCount` bağımsız değişkenini ayrılan arabelleğin boyutuna ayarlaması beklenmektedir. Aşağıdaki örnek, `GetWindowText` işlev bildirimini *Winuser. h*içinde tanımlanan şekilde gösterir.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

`StringBuilder`, `StringBuilder`kapasitesini aşmadığı belirtilen aranan tarafından bir başvuru yapılabilir ve değiştirilebilir. Aşağıdaki kod örneği `StringBuilder` sabit bir uzunluğa nasıl başlatılabileceğinizi gösterir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Dizeleri Hazırlama](marshaling-strings.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
