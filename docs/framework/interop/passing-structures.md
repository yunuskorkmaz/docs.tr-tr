---
title: Yapıları Geçirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 8fde48f0697d986c5fc7f6d7059b6b45a6af1488
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124973"
---
# <a name="passing-structures"></a>Yapıları Geçirme
Birçok yönetilmeyen işlev, işlevine parametre olarak, yapıların üyelerini (Visual Basic içinde Kullanıcı tanımlı türler) veya yönetilen kodda tanımlanan sınıfların üyelerini geçirmenize bekler. Platform Invoke kullanılarak yönetilmeyen koda yapıları veya sınıfları geçirirken, özgün düzeni ve hizalamayı korumak için ek bilgiler sağlamalısınız. Bu konuda, biçimli türleri tanımlamak için kullandığınız <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği tanıtılmaktadır. Yönetilen yapılar ve sınıflar için, **LayoutKind** numaralandırması tarafından sağlanan birkaç öngörülebilir düzen davranışı arasından seçim yapabilirsiniz.  
  
 Bu konu başlığı altında sunulan kavramlara, yapı ve sınıf türleri arasındaki önemli bir fark vardır. Yapılar değer türlerdir ve sınıflardır başvuru türleridir — sınıflar her zaman en az bir bellek yöneltme düzeyi (bir değere işaretçi) sağlar. Yönetilmeyen işlevler, aşağıdaki tablonun ilk sütunundaki imzalarda gösterildiği gibi genellikle dolaylı olarak talep ettiği için bu farklılık önemlidir. Kalan sütunlardaki yönetilen yapı ve sınıf bildirimleri, bildirimindeki yöneltme düzeyini ayarlayabileceğiniz dereceyi gösterir. Bildirimler hem Visual Basic hem de görsel C#için sağlanır.  
  
|Yönetilmeyen imza|Yönetilen bildirim: <br />yöneltme yok<br />`Structure MyType`<br />`struct MyType;`|Yönetilen bildirim: <br />Tek düzeyli yöneltme<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Sıfır yöneltme düzeyini talep edin.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır yöneltme düzeyleri ekler.|Zaten tek bir yöneltme düzeyi olduğundan mümkün değil.|  
|`DoWork(MyType* x);`<br /><br /> Tek düzey yöneltme taleplerini ister.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Tek bir yöneltme düzeyi ekler.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır yöneltme düzeyleri ekler.|  
|`DoWork(MyType** x);`<br /><br /> İki yöneltme düzeyi talep edin.|**ByRef** **byref** veya `ref` `ref` kullanılamadığından mümkün değildir.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Tek bir yöneltme düzeyi ekler.|  
  
 Tablo, platform çağırma bildirimleri için aşağıdaki yönergeleri açıklar:  
  
- Yönetilmeyen işlev yöneltme olmadığında, değer tarafından geçirilen yapıyı kullanın.  
  
- Yönetilmeyen işlev tek bir yöneltme düzeyi talep edildiğinde, başvuruya göre geçirilen bir yapıyı veya değer tarafından geçirilen bir sınıfı kullanın.  
  
- Yönetilmeyen işlev iki yöneltme düzeyi talep edildiğinde başvuruya göre geçirilen bir sınıf kullanın.  
  
## <a name="declaring-and-passing-structures"></a>Yapıları bildirme ve geçirme  
 Aşağıdaki örnek, Yönetilen koddaki `Point` ve `Rect` yapıların nasıl tanımlanacağını gösterir ve türleri parametre olarak User32. dll dosyasındaki **Ptinrect** işlevine iletir. **Pınrect** aşağıdaki yönetilmeyen imzaya sahiptir:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 İşlev bir RECT türüne işaretçi beklediği için rect yapısını başvuruya göre geçirmeniz gerektiğini unutmayın.  
  
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
  
## <a name="declaring-and-passing-classes"></a>Sınıfları bildirme ve geçirme  
 Sınıf, sabit bir üye düzenine sahip olduğu sürece, bir sınıfın üyelerini yönetilmeyen DLL işlevine geçirebilirsiniz. Aşağıdaki örnek, sıralı sırada tanımlanan `MySystemTime` sınıfının üyelerinin, User32. dll dosyasındaki **GetSystemTime** 'a nasıl geçirileceğini gösterir. **GetSystemTime** , şu yönetilmeyen imzaya sahiptir:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Değer türlerinin aksine, sınıfların her zaman en az bir yöneltme düzeyi vardır.  
  
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
