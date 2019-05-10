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
ms.openlocfilehash: e932481496aef7fd0533054316deb32f65e95deb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063199"
---
# <a name="passing-structures"></a>Yapıları Geçirme
Birçok yönetilmeyen işlev, işlev bir parametre olarak yapıları (Visual Basic'te türleri kullanıcı tanımlı) veya yönetilen kod içinde tanımlanan sınıflar üyesi geçirmek için bekler. Yapıları geçirme veya platformu kullanarak yönetilmeyen kod için sınıflar çağırdığınızda, hizalama ve özgün düzeni korumak için ek bilgiler sağlamanız gerekir. Bu konu tanıtır <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türleri tanımlamak için kullanılan öznitelik. Yönetilen yapıları ve sınıfları için tarafından sağlanan bazı öngörülebilir Düzen davranışları aralarından seçim yapabileceğiniz **LayoutKind** sabit listesi.  
  
 Bu konuda sunulan kavramlarına Orta, yapı ve sınıf türleri arasında önemli bir farktır. Yapıları, değer türleri ve başvuru türleri sınıflardır — sınıflar her zaman en az bir (bir değere bir işaretçi) bellek yöneltme düzeyi sağlar. Yönetilmeyen işlevleri yöneltme, genellikle gerektirdiğinden bu fark aşağıdaki tablonun ilk sütunundaki imzaları gösterildiği önemlidir. Sınıf bildirimlerinde ve kalan sütunların ve yönetilen yapısı yöneltme düzeyi, bildiriminde yapabilirsiniz derecesini gösterir. Bildirimleri, Visual Basic ve Visual için sağlanan C#.  
  
|Yönetilmeyen imzası|Yönetilen bildirimi: <br />hiçbir yöneltme<br />`Structure MyType`<br />`struct MyType;`|Yönetilen bildirimi: <br />bir yönlendirme düzeyi<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Talepleri, yöneltme düzeyi sıfır.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır, yöneltme düzeyi ekler.|Zaten bir yöneltme düzeyi olduğundan yapılamaz.|  
|`DoWork(MyType* x);`<br /><br /> Bir düzey yöneltme ihtiyaç duyar.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Yöneltme bir düzey ekler.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Sıfır, yöneltme düzeyi ekler.|  
|`DoWork(MyType** x);`<br /><br /> İki, yöneltme düzeyi ihtiyaç duyar.|Mümkün değildir çünkü **ByRef** **ByRef** veya `ref` `ref` kullanılamaz.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Yöneltme bir düzey ekler.|  
  
 Platform çağırma için bildirimleri tabloda aşağıdaki yönergeleri açıklanmaktadır:  
  
- Yönetilmeyen işlev hiçbir yöneltme talep ettiğinde, değer tarafından geçirilen yapının kullanın.  
  
- Başvuru tarafından geçirilen yapının ya da bir yöneltme düzeyi yönetilmeyen işlev talep ettiğinde, değer olarak geçilemez bir sınıfı kullanın.  
  
- Yönetilmeyen işlev iki, yöneltme düzeyi talep ettiğinde, başvuru tarafından geçirilmediğine bir sınıfı kullanın.  
  
## <a name="declaring-and-passing-structures"></a>Bildirme ve yapıları geçirme  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir `Point` ve `Rect` yapıları, yönetilen kod ve geçiş türleri parametre olarak **PtInRect** User32.dll dosyasındaki işlevi. **PtInRect** aşağıdaki yönetilmeyen imzası:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Dikdörtgen türü için bir işaretçi işlevi bekliyor olduğundan başvuru ile Rect yapısı geçmesi gereken dikkat edin.  
  
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
  
## <a name="declaring-and-passing-classes"></a>Bildirme ve sınıfları geçirme  
 Sabit üye Düzen sınıfı olduğu sürece, bir yönetilmeyen DLL işlevi için bir sınıf üyesi geçirebilirsiniz. Aşağıdaki örnek, üyelerinin geçirilecek gösterilmiştir `MySystemTime` sıralı bir düzende için tanımlanmış olan sınıf **GetSystemTime** User32.dll dosyasında. **GetSystemTime** aşağıdaki yönetilmeyen imzası:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Değer türlerinin aksine, sınıflar her zaman en az bir yöneltme düzeyi var.  
  
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

- [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
