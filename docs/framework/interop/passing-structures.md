---
title: Yapıları Geçirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764916263f6f88615d61badaf2c32807bcc09b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391514"
---
# <a name="passing-structures"></a>Yapıları Geçirme
Birçok yönetilmeyen işlevleri, işlevi parametre olarak yapıları (Visual Basic'te türleri kullanıcı tanımlı) veya yönetilen kod içinde tanımlanan sınıflar üyesi geçirmek için bekler. Yapıları geçirme veya platformu kullanılarak yönetilmeyen kod sınıflarına çağırdığınızda özgün düzeni ve hizalama korumak için ek bilgi sağlamanız gerekir. Bu konu tanıtır <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türlerini tanımlamak için kullandığınız özniteliği. Yönetilen yapılar ve sınıflar için tarafından sağlanan bazı tahmin edilebilir düzeni davranışları aralarından seçim yapabileceğiniz **LayoutKind** numaralandırması.  
  
 Bu konuda sunulan kavramlarına Orta yapısı ve sınıf türleri arasında önemli bir farktır. Değer türleri olan yapıları ve sınıfları başvuru türleri — sınıflar her zaman en az bir düzeyde bellek yöneltme (bir değer için bir işaretçi) sağlar. Yönetilmeyen İşlevler genellikle yöneltme, isteğe bağlı olduğundan aşağıdaki tablonun ilk sütunu imzaları gösterildiği gibi bu fark daha önemlidir. Kalan sütunlar sınıf bildirimlerinde ve yönetilen yapısı için yöneltme düzeyi, bildiriminde ayarlayabilirsiniz derecesini gösterir. Bildirimler hem Visual Basic ve Visual C# için sağlanır.  
  
|Yönetilmeyen imza|Yönetilen bildirimi: <br />hiçbir yöneltme<br />`Structure MyType`<br />`struct MyType;`|Yönetilen bildirimi: <br />bir düzey yöneltme<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Taleplerin yöneltme düzeylerini sıfır.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Yöneltme sıfır düzeylerde ekler.|Zaten yöneltme bir düzey olduğundan yapılamaz.|  
|`DoWork(MyType* x);`<br /><br /> Bir düzey yöneltme ihtiyaç duyar.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Bir düzey yöneltme ekler.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Yöneltme sıfır düzeylerde ekler.|  
|`DoWork(MyType** x);`<br /><br /> Yöneltme iki düzeyde ihtiyaç duyar.|Mümkün değildir çünkü **ByRef** **ByRef** veya `ref` `ref` kullanılamaz.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Bir düzey yöneltme ekler.|  
  
 Platform çağırma için bildirimler tablo aşağıdaki yönergeleri açıklar:  
  
-   Yönetilmeyen işlev hiçbir yöneltme talep ettiğinde değeri tarafından geçirilen bir yapı kullanın.  
  
-   Başvuruya göre geçirilen bir yapı ya da bir sınıf yönetilmeyen işlev yöneltme bir düzey talep ettiğinde değeri tarafından geçirilen kullanın.  
  
-   Yönetilmeyen işlev yöneltme iki düzeyde talep ettiğinde başvuruya göre geçirilen bir sınıf kullanma.  
  
## <a name="declaring-and-passing-structures"></a>Bildirme ve yapıları geçirme  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir `Point` ve `Rect` yapılarda yönetilen kod ve türleri için parametre olarak geçirmek **PtInRect** User32.dll dosyasındaki işlevi. **PtInRect** aşağıdaki yönetilmeyen imzası vardır:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 RECT türü için bir işaretçi işlev bekliyor beri başvuruya göre Rect yapısı geçmesi gereken dikkat edin.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Bildirme ve sınıfları geçirme  
 Sabit üye düzeni sınıfı olduğu sürece bir yönetilmeyen DLL işlevi için bir sınıf üyeleri geçirebilirsiniz. Aşağıdaki örnek üyeleri geçirmek nasıl gösterir `MySystemTime` sıralı bir düzende için tanımlanan sınıfı **GetSystemTime** User32.dll dosyasında. **GetSystemTime** aşağıdaki yönetilmeyen imzası vardır:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Değer türlerinin aksine, sınıflar her zaman yöneltme en az bir düzeyine sahip.  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
