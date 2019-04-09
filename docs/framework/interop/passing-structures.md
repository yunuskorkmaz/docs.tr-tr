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
ms.openlocfilehash: c8e35a09bd3348d5f53c662cf6e0ee9fec733d88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142824"
---
# <a name="passing-structures"></a><span data-ttu-id="a01af-102">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="a01af-102">Passing Structures</span></span>
<span data-ttu-id="a01af-103">Birçok yönetilmeyen işlev, işlev bir parametre olarak yapıları (Visual Basic'te türleri kullanıcı tanımlı) veya yönetilen kod içinde tanımlanan sınıflar üyesi geçirmek için bekler.</span><span class="sxs-lookup"><span data-stu-id="a01af-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="a01af-104">Yapıları geçirme veya platformu kullanarak yönetilmeyen kod için sınıflar çağırdığınızda, hizalama ve özgün düzeni korumak için ek bilgiler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a01af-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="a01af-105">Bu konu tanıtır <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türleri tanımlamak için kullanılan öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a01af-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="a01af-106">Yönetilen yapıları ve sınıfları için tarafından sağlanan bazı öngörülebilir Düzen davranışları aralarından seçim yapabileceğiniz **LayoutKind** sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="a01af-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="a01af-107">Bu konuda sunulan kavramlarına Orta, yapı ve sınıf türleri arasında önemli bir farktır.</span><span class="sxs-lookup"><span data-stu-id="a01af-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="a01af-108">Yapıları, değer türleri ve başvuru türleri sınıflardır — sınıflar her zaman en az bir (bir değere bir işaretçi) bellek yöneltme düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a01af-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="a01af-109">Yönetilmeyen işlevleri yöneltme, genellikle gerektirdiğinden bu fark aşağıdaki tablonun ilk sütunundaki imzaları gösterildiği önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a01af-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="a01af-110">Sınıf bildirimlerinde ve kalan sütunların ve yönetilen yapısı yöneltme düzeyi, bildiriminde yapabilirsiniz derecesini gösterir. Bildirimleri, Visual Basic ve Visual için sağlanan C#.</span><span class="sxs-lookup"><span data-stu-id="a01af-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="a01af-111">Yönetilmeyen imzası</span><span class="sxs-lookup"><span data-stu-id="a01af-111">Unmanaged signature</span></span>|<span data-ttu-id="a01af-112">Yönetilen bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a01af-112">Managed declaration:</span></span> <br /><span data-ttu-id="a01af-113">hiçbir yöneltme</span><span class="sxs-lookup"><span data-stu-id="a01af-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="a01af-114">Yönetilen bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a01af-114">Managed declaration:</span></span> <br /><span data-ttu-id="a01af-115">bir yönlendirme düzeyi</span><span class="sxs-lookup"><span data-stu-id="a01af-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="a01af-116">Talepleri, yöneltme düzeyi sıfır.</span><span class="sxs-lookup"><span data-stu-id="a01af-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a01af-117">Sıfır, yöneltme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="a01af-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="a01af-118">Zaten bir yöneltme düzeyi olduğundan yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="a01af-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="a01af-119">Bir düzey yöneltme ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="a01af-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a01af-120">Yöneltme bir düzey ekler.</span><span class="sxs-lookup"><span data-stu-id="a01af-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a01af-121">Sıfır, yöneltme düzeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="a01af-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="a01af-122">İki, yöneltme düzeyi ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="a01af-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="a01af-123">Mümkün değildir çünkü **ByRef** **ByRef** veya `ref` `ref` kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a01af-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a01af-124">Yöneltme bir düzey ekler.</span><span class="sxs-lookup"><span data-stu-id="a01af-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="a01af-125">Platform çağırma için bildirimleri tabloda aşağıdaki yönergeleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="a01af-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="a01af-126">Yönetilmeyen işlev hiçbir yöneltme talep ettiğinde, değer tarafından geçirilen yapının kullanın.</span><span class="sxs-lookup"><span data-stu-id="a01af-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="a01af-127">Başvuru tarafından geçirilen yapının ya da bir yöneltme düzeyi yönetilmeyen işlev talep ettiğinde, değer olarak geçilemez bir sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a01af-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="a01af-128">Yönetilmeyen işlev iki, yöneltme düzeyi talep ettiğinde, başvuru tarafından geçirilmediğine bir sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a01af-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="a01af-129">Bildirme ve yapıları geçirme</span><span class="sxs-lookup"><span data-stu-id="a01af-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="a01af-130">Aşağıdaki örnek nasıl tanımlanacağını gösterir `Point` ve `Rect` yapıları, yönetilen kod ve geçiş türleri parametre olarak **PtInRect** User32.dll dosyasındaki işlevi.</span><span class="sxs-lookup"><span data-stu-id="a01af-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="a01af-131">**PtInRect** aşağıdaki yönetilmeyen imzası:</span><span class="sxs-lookup"><span data-stu-id="a01af-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="a01af-132">Dikdörtgen türü için bir işaretçi işlevi bekliyor olduğundan başvuru ile Rect yapısı geçmesi gereken dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a01af-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
Friend Class WindowsAPI      
    Friend Shared Declare Auto Function PtInRect Lib "user32.dll" (
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
  
internal static class WindowsAPI
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="a01af-133">Bildirme ve sınıfları geçirme</span><span class="sxs-lookup"><span data-stu-id="a01af-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="a01af-134">Sabit üye Düzen sınıfı olduğu sürece, bir yönetilmeyen DLL işlevi için bir sınıf üyesi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a01af-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="a01af-135">Aşağıdaki örnek, üyelerinin geçirilecek gösterilmiştir `MySystemTime` sıralı bir düzende için tanımlanmış olan sınıf **GetSystemTime** User32.dll dosyasında.</span><span class="sxs-lookup"><span data-stu-id="a01af-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="a01af-136">**GetSystemTime** aşağıdaki yönetilmeyen imzası:</span><span class="sxs-lookup"><span data-stu-id="a01af-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="a01af-137">Değer türlerinin aksine, sınıflar her zaman en az bir yöneltme düzeyi var.</span><span class="sxs-lookup"><span data-stu-id="a01af-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
Friend Class WindowsAPI  
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Shared Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        WindowsAPI.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
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
internal static class WindowsAPI
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
        WindowsAPI.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a01af-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a01af-138">See also</span></span>

- [<span data-ttu-id="a01af-139">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="a01af-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
