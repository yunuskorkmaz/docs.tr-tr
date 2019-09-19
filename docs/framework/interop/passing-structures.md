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
ms.openlocfilehash: eef52827bfe36977c9c4c844f4f431e7404adc97
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051674"
---
# <a name="passing-structures"></a><span data-ttu-id="2ecea-102">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="2ecea-102">Passing Structures</span></span>
<span data-ttu-id="2ecea-103">Birçok yönetilmeyen işlev, işlevine parametre olarak, yapıların üyelerini (Visual Basic içinde Kullanıcı tanımlı türler) veya yönetilen kodda tanımlanan sınıfların üyelerini geçirmenize bekler.</span><span class="sxs-lookup"><span data-stu-id="2ecea-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="2ecea-104">Platform Invoke kullanılarak yönetilmeyen koda yapıları veya sınıfları geçirirken, özgün düzeni ve hizalamayı korumak için ek bilgiler sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2ecea-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="2ecea-105">Bu konuda, biçimli <xref:System.Runtime.InteropServices.StructLayoutAttribute> türleri tanımlamak için kullandığınız özniteliği tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2ecea-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="2ecea-106">Yönetilen yapılar ve sınıflar için, **LayoutKind** numaralandırması tarafından sağlanan birkaç öngörülebilir düzen davranışı arasından seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ecea-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="2ecea-107">Bu konu başlığı altında sunulan kavramlara, yapı ve sınıf türleri arasındaki önemli bir fark vardır.</span><span class="sxs-lookup"><span data-stu-id="2ecea-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="2ecea-108">Yapılar değer türlerdir ve sınıflardır başvuru türleridir — sınıflar her zaman en az bir bellek yöneltme düzeyi (bir değere işaretçi) sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ecea-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="2ecea-109">Yönetilmeyen işlevler, aşağıdaki tablonun ilk sütunundaki imzalarda gösterildiği gibi genellikle dolaylı olarak talep ettiği için bu farklılık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2ecea-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="2ecea-110">Kalan sütunlardaki yönetilen yapı ve sınıf bildirimleri, bildirimindeki yöneltme düzeyini ayarlayabileceğiniz dereceyi gösterir. Bildirimler hem Visual Basic hem de görsel C#için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2ecea-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="2ecea-111">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="2ecea-111">Unmanaged signature</span></span>|<span data-ttu-id="2ecea-112">Yönetilen bildirim:</span><span class="sxs-lookup"><span data-stu-id="2ecea-112">Managed declaration:</span></span> <br /><span data-ttu-id="2ecea-113">yöneltme yok</span><span class="sxs-lookup"><span data-stu-id="2ecea-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="2ecea-114">Yönetilen bildirim:</span><span class="sxs-lookup"><span data-stu-id="2ecea-114">Managed declaration:</span></span> <br /><span data-ttu-id="2ecea-115">Tek düzeyli yöneltme</span><span class="sxs-lookup"><span data-stu-id="2ecea-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="2ecea-116">Sıfır yöneltme düzeyini talep edin.</span><span class="sxs-lookup"><span data-stu-id="2ecea-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="2ecea-117">Sıfır yöneltme düzeyleri ekler.</span><span class="sxs-lookup"><span data-stu-id="2ecea-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="2ecea-118">Zaten tek bir yöneltme düzeyi olduğundan mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="2ecea-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="2ecea-119">Tek düzey yöneltme taleplerini ister.</span><span class="sxs-lookup"><span data-stu-id="2ecea-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="2ecea-120">Tek bir yöneltme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="2ecea-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="2ecea-121">Sıfır yöneltme düzeyleri ekler.</span><span class="sxs-lookup"><span data-stu-id="2ecea-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="2ecea-122">İki yöneltme düzeyi talep edin.</span><span class="sxs-lookup"><span data-stu-id="2ecea-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="2ecea-123">**ByRef** **ByRef** `ref` veya`ref` kullanılamıyor olduğundan mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="2ecea-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="2ecea-124">Tek bir yöneltme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="2ecea-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="2ecea-125">Tablo, platform çağırma bildirimleri için aşağıdaki yönergeleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="2ecea-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="2ecea-126">Yönetilmeyen işlev yöneltme olmadığında, değer tarafından geçirilen yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ecea-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="2ecea-127">Yönetilmeyen işlev tek bir yöneltme düzeyi talep edildiğinde, başvuruya göre geçirilen bir yapıyı veya değer tarafından geçirilen bir sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ecea-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="2ecea-128">Yönetilmeyen işlev iki yöneltme düzeyi talep edildiğinde başvuruya göre geçirilen bir sınıf kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ecea-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="2ecea-129">Yapıları bildirme ve geçirme</span><span class="sxs-lookup"><span data-stu-id="2ecea-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="2ecea-130">Aşağıdaki örnek, yönetilen kodda `Point` ve `Rect` yapıların nasıl tanımlanacağını gösterir ve türleri parametre olarak User32. dll dosyasındaki **ptinrect** işlevine iletir.</span><span class="sxs-lookup"><span data-stu-id="2ecea-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="2ecea-131">**Pınrect** aşağıdaki yönetilmeyen imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2ecea-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="2ecea-132">İşlev bir RECT türüne işaretçi beklediği için rect yapısını başvuruya göre geçirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ecea-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="2ecea-133">Sınıfları bildirme ve geçirme</span><span class="sxs-lookup"><span data-stu-id="2ecea-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="2ecea-134">Sınıf, sabit bir üye düzenine sahip olduğu sürece, bir sınıfın üyelerini yönetilmeyen DLL işlevine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ecea-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="2ecea-135">Aşağıdaki örnek, sıralı sırada tanımlanan `MySystemTime` sınıfın üyelerinin User32. dll dosyasındaki **GetSystemTime** 'a nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ecea-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="2ecea-136">**GetSystemTime** , şu yönetilmeyen imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2ecea-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="2ecea-137">Değer türlerinin aksine, sınıfların her zaman en az bir yöneltme düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="2ecea-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ecea-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ecea-138">See also</span></span>

- [<span data-ttu-id="2ecea-139">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="2ecea-139">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
