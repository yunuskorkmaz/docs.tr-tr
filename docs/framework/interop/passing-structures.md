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
# <a name="passing-structures"></a><span data-ttu-id="9eb7a-102">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="9eb7a-102">Passing Structures</span></span>
<span data-ttu-id="9eb7a-103">Birçok yönetilmeyen işlevleri, işlevi parametre olarak yapıları (Visual Basic'te türleri kullanıcı tanımlı) veya yönetilen kod içinde tanımlanan sınıflar üyesi geçirmek için bekler.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="9eb7a-104">Yapıları geçirme veya platformu kullanılarak yönetilmeyen kod sınıflarına çağırdığınızda özgün düzeni ve hizalama korumak için ek bilgi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="9eb7a-105">Bu konu tanıtır <xref:System.Runtime.InteropServices.StructLayoutAttribute> biçimlendirilmiş türlerini tanımlamak için kullandığınız özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="9eb7a-106">Yönetilen yapılar ve sınıflar için tarafından sağlanan bazı tahmin edilebilir düzeni davranışları aralarından seçim yapabileceğiniz **LayoutKind** numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="9eb7a-107">Bu konuda sunulan kavramlarına Orta yapısı ve sınıf türleri arasında önemli bir farktır.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="9eb7a-108">Değer türleri olan yapıları ve sınıfları başvuru türleri — sınıflar her zaman en az bir düzeyde bellek yöneltme (bir değer için bir işaretçi) sağlar.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="9eb7a-109">Yönetilmeyen İşlevler genellikle yöneltme, isteğe bağlı olduğundan aşağıdaki tablonun ilk sütunu imzaları gösterildiği gibi bu fark daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="9eb7a-110">Kalan sütunlar sınıf bildirimlerinde ve yönetilen yapısı için yöneltme düzeyi, bildiriminde ayarlayabilirsiniz derecesini gösterir. Bildirimler hem Visual Basic ve Visual C# için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="9eb7a-111">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="9eb7a-111">Unmanaged signature</span></span>|<span data-ttu-id="9eb7a-112">Yönetilen bildirimi:</span><span class="sxs-lookup"><span data-stu-id="9eb7a-112">Managed declaration:</span></span> <br /><span data-ttu-id="9eb7a-113">hiçbir yöneltme</span><span class="sxs-lookup"><span data-stu-id="9eb7a-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="9eb7a-114">Yönetilen bildirimi:</span><span class="sxs-lookup"><span data-stu-id="9eb7a-114">Managed declaration:</span></span> <br /><span data-ttu-id="9eb7a-115">bir düzey yöneltme</span><span class="sxs-lookup"><span data-stu-id="9eb7a-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="9eb7a-116">Taleplerin yöneltme düzeylerini sıfır.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="9eb7a-117">Yöneltme sıfır düzeylerde ekler.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="9eb7a-118">Zaten yöneltme bir düzey olduğundan yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="9eb7a-119">Bir düzey yöneltme ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="9eb7a-120">Bir düzey yöneltme ekler.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="9eb7a-121">Yöneltme sıfır düzeylerde ekler.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="9eb7a-122">Yöneltme iki düzeyde ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="9eb7a-123">Mümkün değildir çünkü **ByRef** **ByRef** veya `ref` `ref` kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="9eb7a-124">Bir düzey yöneltme ekler.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="9eb7a-125">Platform çağırma için bildirimler tablo aşağıdaki yönergeleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="9eb7a-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="9eb7a-126">Yönetilmeyen işlev hiçbir yöneltme talep ettiğinde değeri tarafından geçirilen bir yapı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="9eb7a-127">Başvuruya göre geçirilen bir yapı ya da bir sınıf yönetilmeyen işlev yöneltme bir düzey talep ettiğinde değeri tarafından geçirilen kullanın.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="9eb7a-128">Yönetilmeyen işlev yöneltme iki düzeyde talep ettiğinde başvuruya göre geçirilen bir sınıf kullanma.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="9eb7a-129">Bildirme ve yapıları geçirme</span><span class="sxs-lookup"><span data-stu-id="9eb7a-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="9eb7a-130">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir `Point` ve `Rect` yapılarda yönetilen kod ve türleri için parametre olarak geçirmek **PtInRect** User32.dll dosyasındaki işlevi.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="9eb7a-131">**PtInRect** aşağıdaki yönetilmeyen imzası vardır:</span><span class="sxs-lookup"><span data-stu-id="9eb7a-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="9eb7a-132">RECT türü için bir işaretçi işlev bekliyor beri başvuruya göre Rect yapısı geçmesi gereken dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="9eb7a-133">Bildirme ve sınıfları geçirme</span><span class="sxs-lookup"><span data-stu-id="9eb7a-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="9eb7a-134">Sabit üye düzeni sınıfı olduğu sürece bir yönetilmeyen DLL işlevi için bir sınıf üyeleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="9eb7a-135">Aşağıdaki örnek üyeleri geçirmek nasıl gösterir `MySystemTime` sıralı bir düzende için tanımlanan sınıfı **GetSystemTime** User32.dll dosyasında.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="9eb7a-136">**GetSystemTime** aşağıdaki yönetilmeyen imzası vardır:</span><span class="sxs-lookup"><span data-stu-id="9eb7a-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="9eb7a-137">Değer türlerinin aksine, sınıflar her zaman yöneltme en az bir düzeyine sahip.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9eb7a-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9eb7a-138">See Also</span></span>  
 [<span data-ttu-id="9eb7a-139">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="9eb7a-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
