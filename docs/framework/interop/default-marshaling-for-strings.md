---
title: Dizeler için Varsayılan Sıralama
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
ms.openlocfilehash: 88604058bd460d80214be6051abef7dc561c7710
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394913"
---
# <a name="default-marshaling-for-strings"></a>Dizeler için Varsayılan Hazırlama
Hem <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfları, benzer hazırlama davranışı sahiptir.  
  
 Dizeleri COM stil olarak sıralanmış `BSTR` tür veya null ile sonlandırılmış bir dize (bir null karakter ile biten bir karakter dizisi) olarak. Dizedeki karakterleri Unicode (Windows sistemlerinde varsayılan) veya ANSI olarak sıralanabilir.  
  
 Bu konu, dize türlerini hazırlama hakkında aşağıdaki bilgileri sağlar:  
  
-   [Arabirimlerde kullanılan dizeleri](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Platform kullanılan dizeleri çağırma](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Yapılarda kullanılan dizeleri](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Sabit uzunluklu dize arabellekler](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>Arabirimlerde kullanılan dizeleri  
 Yönetilmeyen kod bir yöntem bağımsız değişkeni olarak sıralanmış zaman dize veri türü için hazırlama seçenekleri aşağıdaki tabloda gösterilmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri COM arabirimlerine dizelerini sıralama için.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (varsayılan)|COM Stili `BSTR` önekli uzunluğu ve Unicode karakterler.|  
|`UnmanagedType.LPStr`|ANSI karakter null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.LPWStr`|Unicode karakterler null ile sonlandırılmış bir dizi için bir işaretçi.|  
  
 Bu tablo dizelere uygulanır. Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `UnmanagedType.LPStr` ve `UnmanagedType.LPWStr`.  
  
 Aşağıdaki örnek, bildirilen dizeleri gösterir `IStringWorker` arabirimi.  
  
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

Aşağıdaki örnek, bir tür kitaplığı'nda açıklanan karşılık gelen arabirimi gösterir.

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

## <a name="strings-used-in-platform-invoke"></a>Platform kullanılan dizeleri çağırma  
 Platform çağırma kopyaları dize bağımsız değişkeni, .NET Framework biçimi (Unicode) platformu yönetilmeyen biçimine dönüştürme. Dizeleri sabittir ve çağrısı döndürüldüğünde geri yönetilmeyen bellekten yönetilen bellek kopyalanmaz.  
  
 Aşağıdaki tabloda bir yöntem bağımsız değişkeni bir platform çağırma gibi çağrısı sıralanmış zaman dizeleri sıralama seçeneklerini listeler. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için dizeleri sıralama.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|COM Stili `BSTR` önekli uzunluğu ve ANSI karakter.|  
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli uzunluğu ve Unicode karakterler.|  
|`UnmanagedType.LPStr`|ANSI karakter null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.LPTStr`|Platforma bağımlı karakter null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.LPWStr`|Unicode karakterler null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.TBStr`|COM Stili `BSTR` önekli uzunluğu ve platforma bağımlı karakter.|  
|`VBByRefStr`|Bir dizede değiştirmek için Visual Basic .NET sağlayan bir değer kodu yönetilmeyen ve sonuçları yönetilen kodda yansıtılmasını. Bu değer yalnızca platform çağırma için desteklenir. Visual Basic için varsayılan değer budur `ByVal` dizeleri.|  
  
 Bu tablo dizelere uygulanır. Ancak, <xref:System.Text.StringBuilder>, izin verilen tek Seçenekler `LPStr`, `LPTStr`, ve `LPWStr`.  
  
 Aşağıdaki tür tanımı doğru kullanımı gösterilmiştir `MarshalAsAttribute` çağrıları için platform çağırma.  
  
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
## <a name="strings-used-in-structures"></a>Yapılarda kullanılan dizeleri  
 Dizeleri yapıları geçerli üyesi; Ancak, <xref:System.Text.StringBuilder> arabellekleri yapılarda geçersiz. Aşağıdaki tabloda türü bir alan olarak sıralanmış dize veri türü için hazırlama seçenekleri gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri için bir alana dizelerini sıralama.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|COM Stili `BSTR` önekli uzunluğu ve Unicode karakterler.|  
|`UnmanagedType.LPStr`|ANSI karakter null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.LPTStr`|Platforma bağımlı karakter null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.LPWStr`|Unicode karakterler null ile sonlandırılmış bir dizi için bir işaretçi.|  
|`UnmanagedType.ByValTStr`|Karakter sabit uzunluk dizisi; dizinin türü içeren yapısı karakter kümesi tarafından belirlenir.|  
  
 `ByValTStr` Türü satır içi, bir yapı içinde görünür sabit uzunluklu karakter dizileri için kullanılır. Diğer türleri dizeleri işaretçileri içeren yapılarını içindeki dize başvurular için geçerlidir.  
  
 `CharSet` Bağımsız değişkeni <xref:System.Runtime.InteropServices.StructLayoutAttribute> içeren yapısına uygulanan özniteliği yapıları dizelerde karakter biçimini belirler. Aşağıdaki örnek yapıları dize başvuruları ve satır içi dizeleri yanı sıra ANSI, Unicode ve platforma bağımlı karakterleri içermelidir.  
  
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
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> farklı biçimlerde aynı yapısını tanımlamak için öznitelik.  
  
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
## <a name="fixed-length-string-buffers"></a>Sabit uzunluklu dize arabellekler  
 Bazı durumlarda, bir sabit uzunlukta karakter arabellek yönetilebilmesini yönetilmeyen koda geçirilmelidir. Aranan geçirilen arabellek içeriğini değiştirilemiyor çünkü sadece bir dizeye geçiliyor bu durumda geçerli değildir. Dize başvuruya göre geçirilen olsa bile, verilen boyuta arabelleği başlatılamadı yolu yoktur.  
  
 Çözüm geçirmektir bir <xref:System.Text.StringBuilder> yerine bir dize bağımsız değişkeni olarak arabellek. A `StringBuilder` başvuru yapıldı ve kapasitesini aşmayan sağlanan Aranan tarafından değiştirilmiş `StringBuilder`. Sabit uzunluk için de yeniden başlatılabilir. Örneğin, başlatma, bir `StringBuilder` kapasitesine arabelleğe `N`, Sıralayıcı bir arabellek boyutunu sağlar (`N`+ 1) karakter. Yönetilmeyen dizesi çalışırken null Sonlandırıcı içeriyor olgusu + 1 hesaplar `StringBuilder` desteklemez.  
  
 Örneğin, Microsoft Win32 API `GetWindowText` (Windows.h içinde tanımlanan) yönetilebilmesini yönetilmeyen koda geçirilmelidir sabit uzunlukta karakter arabellek işlevdir. `LpString` gösterdiği için çağıranın ayrılan arabellek boyutunu `nMaxCount`. Arayan arabellek ayırın ve ayarlamak için beklenen `nMaxCount` bağımsız değişkeni için ayrılan arabellek boyutu. Aşağıdaki kodda gösterildiği `GetWindowText` Windows.h içinde tanımlanan işlevi bildiriminde.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` başvuru yapıldı ve kapasitesini aşmayan sağlanan Aranan tarafından değiştirilmiş `StringBuilder`. Aşağıdaki kod örneğinde gösterilmektedir nasıl `StringBuilder` sabit uzunlukta başlatılabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)  
 [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)  
 [Tek yönlü öznitelikleri](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [Kopyalama ve Sabitleme](copying-and-pinning.md)
