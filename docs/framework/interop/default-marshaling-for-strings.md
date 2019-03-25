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
ms.openlocfilehash: aeba97a5caef8fc705a3b04496ce1fd17085ec5d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409321"
---
# <a name="default-marshaling-for-strings"></a>Dizeler için Varsayılan Hazırlama
Hem <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflar benzer hazırlama davranışı sahiptir.  
  
 Dizeleri bir COM stili olarak sıralanmış `BSTR` türü veya null ile sonlandırılmış bir dize (boş bir karakter ile sona eren bir karakter dizisi) olarak. Unicode (Windows sistemlerinde varsayılan) veya ANSI olarak dize içindeki karakterlerin sıralanabilir.  
  
 Bu konu, dize türlerini hazırlama hakkında aşağıdaki bilgileri sağlar:  
  
-   [Arabirimlerde kullanılan dizeler](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Dizeleri platformunda kullanılan çağırma](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Yapıları, kullanılan dizeler](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Sabit uzunluklu dize arabelleği](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>Arabirimlerde kullanılan dizeler  
 Aşağıdaki tablo, yönetilmeyen kodu bir metot bağımsız değişkeni olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için COM arabirimlerine dizelerini sıralama.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (varsayılan)|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|  
|`UnmanagedType.LPStr`|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|  
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|  
  
 Bu tablo, dizeleri için geçerlidir. Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.  
  
 Aşağıdaki örnek, dizeleri bildirilen gösterir `IStringWorker` arabirimi.  
  
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

Aşağıdaki örnek, bir tür kitaplığında tanımlanan karşılık gelen arabirimi gösterir.

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

## <a name="strings-used-in-platform-invoke"></a>Dizeleri platformunda kullanılan çağırma  
 Platform çağırma kopyaları dize bağımsız değişkenleri, .NET Framework biçimden (Unicode) platform yönetilmeyen biçimine dönüştürme. Dizeleri sabittir ve yönetilmeyen belleğin geri çağrısı döndürüldüğünde yönetilen bellek kopyalanmaz.  
  
 Aşağıdaki tabloda bir yöntemi bağımsız değişken bir platform çağırma olarak çağrı sıralandığı zaman dizeler için sıralama seçenekleri listeler. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi dizelerini sıralama için değerler.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|COM Stili `BSTR` önekli bir uzunluk ve ANSI karakterler.|  
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|  
|`UnmanagedType.LPStr`|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|  
|`UnmanagedType.LPTStr`|Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.|  
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|  
|`UnmanagedType.TBStr`|COM Stili `BSTR` önekli bir uzunluk ve platforma bağımlı karakter.|  
|`VBByRefStr`|Bir dizede değiştirilecek Visual Basic .NET sağlayan bir değer kod yönetilmeyen ve yönetilen kodda sonuçları yansıtılmasını. Bu değer, yalnızca platform çağırma için desteklenir. Visual Basic için varsayılan değer budur `ByVal` dizeleri.|  
  
 Bu tablo, dizeleri için geçerlidir. Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `LPStr`, `LPTStr`, ve `LPWStr`.  
  
 Aşağıdaki tür tanımı doğru kullanımını gösterir `MarshalAsAttribute` çağrıları için platform çağırma.  
  
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
## <a name="strings-used-in-structures"></a>Yapıları, kullanılan dizeler  
 Dizeleri yapıları geçerli üyeleridir; Ancak, <xref:System.Text.StringBuilder> arabellekler yapılarda geçersiz. Aşağıdaki tabloda, türü, bir alan olarak sıralandığı zaman dize veri türü için sıralama seçeneklerini gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için bir alan için dizeleri sıralama.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli bir uzunluk ve Unicode karakter.|  
|`UnmanagedType.LPStr`|Null ile sonlandırılmış bir dizi ANSI karakter işaretçisi.|  
|`UnmanagedType.LPTStr`|Null ile sonlandırılmış bir dizi platform bağımlı karakter işaretçisi.|  
|`UnmanagedType.LPWStr`|Null ile sonlandırılmış bir dizi Unicode karakter işaretçisi.|  
|`UnmanagedType.ByValTStr`|Karakter sabit uzunluklu dizi; dizi türü içeren yapı karakter kümesi tarafından belirlenir.|  
  
 `ByValTStr` Türü satır içi, bir yapı içinde görünen sabit uzunluklu karakteri diziler için kullanılır. Diğer türleri dizelerine içeren yapıları içindeki dize başvuruları için geçerlidir.  
  
 `CharSet` Bağımsız değişkeni <xref:System.Runtime.InteropServices.StructLayoutAttribute> içeren yapı için uygulanan bir öznitelik yapılardaki dize karakter biçimini belirler. Aşağıdaki örnek yapılardaki dize başvurular ve satır içi dizeleri yanı sıra ANSI, Unicode ve platforma bağımlı karakter içerir.  
  
### <a name="type-library-representation"></a>Tür kitaplığı gösterimi  
  
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
  
 Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapısını tanımlayan öznitelik.  
  
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
## <a name="fixed-length-string-buffers"></a>Sabit uzunluklu dize arabelleği  
 Bazı durumlarda, sabit uzunluklu karakteri arabellek yönetilebilmesini yönetilmeyen koda geçirilmelidir. Çağrılan geçirilen arabellek içeriği değiştirilemez çünkü yalnızca bir dizeye geçiliyor bu durumda çalışmaz. Dize başvuruya göre geçirilse bile, verilen boyuta arabellek başlatmak için hiçbir yolu yoktur.  
  
 Çözüm geçirmektir bir <xref:System.Text.StringBuilder> bağımsız değişkeni bir dize yerine arabellek. A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`. Sabit uzunluk için de yeniden başlatılabilir. Örneğin, başlatma, bir `StringBuilder` kapasitesi arabelleğe `N`, Sıralayıcı bir arabellek boyutunu sağlar (`N`+ 1) karakter. Yönetilmeyen dize bir null Sonlandırıcı çalışırken sahip olgu + 1 hesaplar `StringBuilder` desteklemez.  
  
 Örneğin, Microsoft Windows API `GetWindowText` (Windows.h içinde tanımlanmıştır) yönetilebilmesini yönetilmeyen koda geçirilmelidir sabit uzunluklu karakteri arabellek işlevdir. `LpString` işaret boyutu arayana ayrılan arabelleğe `nMaxCount`. Çağıranın arabellek ayırmak ve ayarlamak için beklenen `nMaxCount` bağımsız değişkeni için ayrılan arabelleğin boyutu. Aşağıdaki kodda gösterildiği `GetWindowText` işlevi bildiriminde Windows.h içinde tanımlanan.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` başvurusu ve kapasitesini aşmadığından sağlanan Aranan tarafından değiştirilen `StringBuilder`. Aşağıdaki kod örneğinde nasıl `StringBuilder` sabit uzunluk için başlatılabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
