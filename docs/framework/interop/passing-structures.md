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
# <a name="passing-structures"></a><span data-ttu-id="6fe93-102">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="6fe93-102">Passing Structures</span></span>
<span data-ttu-id="6fe93-103">Birçok yönetilmeyen işlev, işlevin parametresi olarak, yapıların üyeleri (Visual Basic'te kullanıcı tanımlı türler) veya yönetilen kodda tanımlanan sınıfların üyeleri olarak geçmenizi bekler.</span><span class="sxs-lookup"><span data-stu-id="6fe93-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="6fe93-104">Yapıları veya sınıfları platform çağırıcıkullanarak yönetilmeyen koda geçerken, özgün düzeni ve hizalamayı korumak için ek bilgiler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="6fe93-105">Bu konu, <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türleri tanımlamak için kullandığınız özniteliği tanır.</span><span class="sxs-lookup"><span data-stu-id="6fe93-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="6fe93-106">Yönetilen yapılar ve sınıflar **için, LayoutKind** numaralandırması tarafından sağlanan birkaç öngörülebilir düzen davranışı arasından seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fe93-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="6fe93-107">Bu konuda sunulan kavramların merkezinde yapı ve sınıf türleri arasında önemli bir fark vardır.</span><span class="sxs-lookup"><span data-stu-id="6fe93-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="6fe93-108">Yapılar değer türleridir ve sınıflar başvuru türleridir — sınıflar her zaman en az bir bellek yönlendirme düzeyi (bir değer işaretçisi) sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fe93-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="6fe93-109">Yönetilmeyen işlevler genellikle aşağıdaki tablonun ilk sütunundaki imzalarda gösterildiği gibi, genellikle yönlendirme gerektirdiğinden, bu fark önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="6fe93-110">Kalan sütunlarda yönetilen yapı ve sınıf bildirimleri, bildiriminizdeki yön düzeyini ayarlama derecenizi gösterir. Görsel Temel ve Görsel C# bildirimleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6fe93-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="6fe93-111">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="6fe93-111">Unmanaged signature</span></span>|<span data-ttu-id="6fe93-112">Yönetilen bildirim:</span><span class="sxs-lookup"><span data-stu-id="6fe93-112">Managed declaration:</span></span> <br /><span data-ttu-id="6fe93-113">yön yok</span><span class="sxs-lookup"><span data-stu-id="6fe93-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="6fe93-114">Yönetilen bildirim:</span><span class="sxs-lookup"><span data-stu-id="6fe93-114">Managed declaration:</span></span> <br /><span data-ttu-id="6fe93-115">bir yön</span><span class="sxs-lookup"><span data-stu-id="6fe93-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="6fe93-116">Sıfır yönlendirme seviyesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="6fe93-117">Sıfır yönlendirme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="6fe93-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="6fe93-118">Zaten bir yönlendirme düzeyi olduğundan mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="6fe93-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="6fe93-119">Bir seviye yönlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="6fe93-120">Bir yönlendirme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="6fe93-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="6fe93-121">Sıfır yönlendirme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="6fe93-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="6fe93-122">İki seviyede yönlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="6fe93-123">**ByRef ByRef** **ByRef** veya `ref` `ref` kullanılamaz çünkü mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="6fe93-124">Bir yönlendirme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="6fe93-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="6fe93-125">Tablo, platform çağırma bildirimleri için aşağıdaki yönergeleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="6fe93-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="6fe93-126">Yönetilmeyen işlev yönlendirme gerektirdiğinde değer tarafından geçirilen bir yapı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fe93-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="6fe93-127">Yönetilmeyen işlev bir yönlendirme düzeyi gerektirdiğinde, başvuru tarafından geçirilen bir yapı yı veya değertarafından geçirilen bir sınıf kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fe93-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="6fe93-128">Yönetilmeyen işlev iki yönlendirme düzeyi gerektirdiğinde başvuru tarafından geçirilen bir sınıf kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fe93-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="6fe93-129">Beyan ve Geçen Yapılar</span><span class="sxs-lookup"><span data-stu-id="6fe93-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="6fe93-130">Aşağıdaki örnek, yönetilen `Point` koddaki `Rect` yapıları ve yapıları nasıl tanımlayacaklarını ve türleri kullanıcı32.dll dosyasındaki **PtInRect** işlevine parametre olarak nasıl geçireceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="6fe93-131">**PtInRect** aşağıdaki yönetilmeyen imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6fe93-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="6fe93-132">İşlev BIR RECt türüne işaretçi beklediğinden, Rect yapısını referans olarak geçmeniz gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6fe93-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="6fe93-133">Beyan ve Geçen Dersler</span><span class="sxs-lookup"><span data-stu-id="6fe93-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="6fe93-134">Sınıfın sabit bir üye düzeni olduğu sürece, sınıfın üyelerini yönetilmeyen bir DLL işlevine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fe93-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="6fe93-135">Aşağıdaki örnek, sıralı sırada tanımlanan `MySystemTime` sınıfın üyelerinin User32.dll dosyasındaki **GetSystemTime'a** nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="6fe93-136">**GetSystemTime** aşağıdaki yönetilmeyen imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6fe93-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="6fe93-137">Değer türlerinden farklı olarak, sınıflar her zaman en az bir yönlendirme düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6fe93-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6fe93-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fe93-138">See also</span></span>

- [<span data-ttu-id="6fe93-139">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="6fe93-139">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
