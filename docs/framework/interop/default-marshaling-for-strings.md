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
# <a name="default-marshaling-for-strings"></a>Dizeler için Varsayılan Hazırlama

Hem <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflar benzer hazırlama davranışı sahiptir.

Dizeleri bir COM stili olarak sıralanmış `BSTR` türü veya null ile sonlandırılmış bir dize (boş bir karakter ile sona eren bir karakter dizisi) olarak. Unicode (Windows sistemlerinde varsayılan) veya ANSI olarak dize içindeki karakterlerin sıralanabilir.

## <a name="strings-used-in-interfaces"></a>Arabirimlerde kullanılan dizeler

Aşağıdaki tablo, yönetilmeyen kodu bir metot bağımsız değişkeni olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için COM arabirimlerine dizelerini sıralama.

|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (varsayılan)|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|
|`UnmanagedType.LPStr`|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|

Bu tabloda uygulandığı <xref:System.String>. İçin <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.

Aşağıdaki örnek, dizeleri bildirilen gösterir `IStringWorker` arabirimi.

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

Aşağıdaki örnek, bir tür kitaplığında tanımlanan karşılık gelen arabirimi gösterir.

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

## <a name="strings-used-in-platform-invoke"></a>Dizeleri platformunda kullanılan çağırma

Platform çağırma kopyaları dize bağımsız değişkenleri, .NET Framework biçimden (Unicode) platform yönetilmeyen biçimine dönüştürme. Dizeleri sabittir ve yönetilmeyen belleğin geri çağrısı döndürüldüğünde yönetilen bellek kopyalanmaz.

Aşağıdaki tabloda bir yöntemi bağımsız değişken bir platform çağırma olarak çağrı sıralandığı zaman dizeler için sıralama seçenekleri listeler. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi dizelerini sıralama için değerler.

|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|COM Stili `BSTR` önekli bir uzunluk ve ANSI karakterler.|
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|
|`UnmanagedType.LPStr` (varsayılan)|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|
|`UnmanagedType.LPTStr`|Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.|
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|
|`UnmanagedType.TBStr`|COM Stili `BSTR` önekli bir uzunluk ve platforma bağımlı karakter.|
|`VBByRefStr`|Bir dizede değiştirilecek Visual Basic .NET sağlayan bir değer kod yönetilmeyen ve yönetilen kodda sonuçları yansıtılmasını. Bu değer, yalnızca platform çağırma için desteklenir. Visual Basic için varsayılan değer budur `ByVal` dizeleri.|

Bu tabloda uygulandığı <xref:System.String>. İçin <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `LPStr`, `LPTStr`, ve `LPWStr`.

Aşağıdaki tür tanımı doğru kullanımını gösterir `MarshalAsAttribute` çağrıları için platform çağırma.

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

## <a name="strings-used-in-structures"></a>Yapıları, kullanılan dizeler

Dizeleri yapıları geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekler yapılarda geçersiz. Sıralama seçenekleri aşağıdaki tabloda gösterilmektedir <xref:System.String> veri türü, bir alan olarak sıralandığı zaman türü. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için bir alan için dizeleri sıralama.

|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|
|`UnmanagedType.LPStr` (varsayılan)|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|
|`UnmanagedType.LPTStr`|Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.|
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|
|`UnmanagedType.ByValTStr`|Karakter sabit uzunluklu dizi; dizi türü içeren yapı karakter kümesi tarafından belirlenir.|

`ByValTStr` Türü satır içi, bir yapı içinde görünen sabit uzunluklu karakteri diziler için kullanılır. Diğer türleri dizelerine içeren yapıları içindeki dize başvuruları için geçerlidir.

`CharSet` Bağımsız değişkeni <xref:System.Runtime.InteropServices.StructLayoutAttribute> içeren uygulanan yapısı yapılardaki dize karakter biçimini belirler. Aşağıdaki örnek yapılardaki dize başvurular ve satır içi dizeleri yanı sıra ANSI, Unicode ve platforma bağımlı karakter içerir. Bu yapılar, tür kitaplığındaki gösterimini aşağıda gösterilir C++ kod:

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

Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapısını tanımlamak için.

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

## <a name="fixed-length-string-buffers"></a>Sabit uzunluklu dize arabelleği

Bazı durumlarda, sabit uzunluklu karakteri arabellek yönetilebilmesini yönetilmeyen koda geçirilmelidir. Çağrılan geçirilen arabellek içeriği değiştirilemez çünkü yalnızca bir dizeye geçiliyor bu durumda çalışmaz. Dize başvuruya göre geçirilse bile, verilen boyuta arabellek başlatmak için hiçbir yolu yoktur.

Çözüm geçirmektir bir <xref:System.Text.StringBuilder> arabellek yerine bağımsız değişken olarak bir <xref:System.String>. A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`. Sabit uzunluk için de yeniden başlatılabilir. Örneğin, başlatma, bir `StringBuilder` kapasitesi arabelleğe `N`, Sıralayıcı bir arabellek boyutunu sağlar (`N`+ 1) karakter. Yönetilmeyen dize bir null Sonlandırıcı çalışırken sahip olgu + 1 hesaplar `StringBuilder` desteklemez.

Örneğin, Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API işlevi (tanımlanan *Windows.h*) arayan işlev Yazar pencerenin metin sabit uzunluklu karakteri arabellek geçmesini gerektirir. `LpString` işaret boyutu arayana ayrılan arabelleğe `nMaxCount`. Çağıranın arabellek ayırmak ve ayarlamak için beklenen `nMaxCount` bağımsız değişkeni için ayrılan arabelleğin boyutu. Aşağıdaki örnekte gösterildiği `GetWindowText` işlevi bildiriminde tanımlanan *Windows.h*.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`. Aşağıdaki kod örneğinde nasıl `StringBuilder` sabit uzunluk için başlatılabilir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Dizeleri Hazırlama](marshaling-strings.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
