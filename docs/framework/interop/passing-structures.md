---
title: Yapıları Geçirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 11e329fa8f0c059b6c2f1c8ccb1d6bd0d0f0030a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181332"
---
# <a name="passing-structures"></a>Yapıları Geçirme
Birçok yönetilmeyen işlev, işlevin parametresi olarak, yapıların üyeleri (Visual Basic'te kullanıcı tanımlı türler) veya yönetilen kodda tanımlanan sınıfların üyeleri olarak geçmenizi bekler. Yapıları veya sınıfları platform çağırıcıkullanarak yönetilmeyen koda geçerken, özgün düzeni ve hizalamayı korumak için ek bilgiler sağlamanız gerekir. Bu konu, <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türleri tanımlamak için kullandığınız özniteliği tanır. Yönetilen yapılar ve sınıflar **için, LayoutKind** numaralandırması tarafından sağlanan birkaç öngörülebilir düzen davranışı arasından seçim yapabilirsiniz.  
  
 Bu konuda sunulan kavramların merkezinde yapı ve sınıf türleri arasında önemli bir fark vardır. Yapılar değer türleridir ve sınıflar başvuru türleridir — sınıflar her zaman en az bir bellek yönlendirme düzeyi (bir değer işaretçisi) sağlar. Yönetilmeyen işlevler genellikle aşağıdaki tablonun ilk sütunundaki imzalarda gösterildiği gibi, genellikle yönlendirme gerektirdiğinden, bu fark önemlidir. Kalan sütunlarda yönetilen yapı ve sınıf bildirimleri, bildiriminizdeki yön düzeyini ayarlama derecenizi gösterir. Görsel Temel ve Görsel C# bildirimleri sağlanır.  
  
|Yönetilmeyen imza|Yönetilen bildirim: <br />yön yok<br />`Structure MyType`<br />`struct MyType;`|Yönetilen bildirim: <br />bir yön<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Sıfır yönlendirme seviyesi gerektirir.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır yönlendirme düzeyi ekler.|Zaten bir yönlendirme düzeyi olduğundan mümkün değil.|  
|`DoWork(MyType* x);`<br /><br /> Bir seviye yönlendirme gerektirir.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Bir yönlendirme düzeyi ekler.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır yönlendirme düzeyi ekler.|  
|`DoWork(MyType** x);`<br /><br /> İki seviyede yönlendirme gerektirir.|**ByRef ByRef** **ByRef** veya `ref` `ref` kullanılamaz çünkü mümkün değildir.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Bir yönlendirme düzeyi ekler.|  
  
 Tablo, platform çağırma bildirimleri için aşağıdaki yönergeleri açıklar:  
  
- Yönetilmeyen işlev yönlendirme gerektirdiğinde değer tarafından geçirilen bir yapı kullanın.  
  
- Yönetilmeyen işlev bir yönlendirme düzeyi gerektirdiğinde, başvuru tarafından geçirilen bir yapı yı veya değertarafından geçirilen bir sınıf kullanın.  
  
- Yönetilmeyen işlev iki yönlendirme düzeyi gerektirdiğinde başvuru tarafından geçirilen bir sınıf kullanın.  
  
## <a name="declaring-and-passing-structures"></a>Beyan ve Geçen Yapılar  
 Aşağıdaki örnek, yönetilen `Point` koddaki `Rect` yapıları ve yapıları nasıl tanımlayacaklarını ve türleri kullanıcı32.dll dosyasındaki **PtInRect** işlevine parametre olarak nasıl geçireceğini gösterir. **PtInRect** aşağıdaki yönetilmeyen imzaya sahiptir:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 İşlev BIR RECt türüne işaretçi beklediğinden, Rect yapısını referans olarak geçmeniz gerektiğine dikkat edin.  
  
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
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
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
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Beyan ve Geçen Dersler  
 Sınıfın sabit bir üye düzeni olduğu sürece, sınıfın üyelerini yönetilmeyen bir DLL işlevine geçirebilirsiniz. Aşağıdaki örnek, sıralı sırada tanımlanan `MySystemTime` sınıfın üyelerinin User32.dll dosyasındaki **GetSystemTime'a** nasıl geçirileceğini gösterir. **GetSystemTime** aşağıdaki yönetilmeyen imzaya sahiptir:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Değer türlerinden farklı olarak, sınıflar her zaman en az bir yönlendirme düzeyine sahiptir.  
  
```vb  
Imports System.Runtime.InteropServices  
  
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
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
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
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DLL İşlevini Çağırma](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
