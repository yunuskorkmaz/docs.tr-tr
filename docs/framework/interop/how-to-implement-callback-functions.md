---
title: "Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5be0dbb6666da88897ceedf0757e2af720705a07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="29269-102">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="29269-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="29269-103">Aşağıdaki yordamı ve örnek platformu kullanılarak yönetilen bir uygulamanın nasıl çağırma göstermek, her pencere tanıtıcısı değeri yerel bilgisayarda yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29269-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="29269-104">Özellikle, yordam ve örnek kullanım **EnumWindows** işlev adıma windows ve yönetilen geri çağırma işlevi adlandırılmış (bir pencere tanıtıcının değerini yazdırmak için geri çağırma) listesi aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="29269-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="29269-105">Bir geri çağırma işlevini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="29269-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="29269-106">İmza için bakabilir **EnumWindows** başka bir uygulama ile geçmeden önce işlevi.</span><span class="sxs-lookup"><span data-stu-id="29269-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="29269-107">**EnumWindows** aşağıdaki imzası vardır:</span><span class="sxs-lookup"><span data-stu-id="29269-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="29269-108">Bu işlev bir geri çağırma gerektiren bir ipucu olan varlığını **lpEnumFunc** bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="29269-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="29269-109">Yaygın **lp** (uzun işaretçisi) öneki birlikte **Func** bir geri çağırma işlevini gösteren bir işaretçi ele bağımsız değişken adına soneki.</span><span class="sxs-lookup"><span data-stu-id="29269-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="29269-110">Win32 işlevleri ile ilgili belgeler için Microsoft Platformu SDK'sı bakın.</span><span class="sxs-lookup"><span data-stu-id="29269-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="29269-111">Yönetilen geri çağırma işlevi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="29269-111">Create the managed callback function.</span></span> <span data-ttu-id="29269-112">Örnek olarak adlandırılan bir temsilci türü bildirir `CallBack`, iki bağımsız değişkeni alır (**hwnd** ve **lparam**).</span><span class="sxs-lookup"><span data-stu-id="29269-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="29269-113">İlk bağımsız değişkeni bir tanıtıcı penceresine değil; İkinci bağımsız değişkeni uygulama tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="29269-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="29269-114">Bu sürümde, her iki değişken tamsayı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29269-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="29269-115">Geri arama işlevleri genellikle başarı ve başarısızlık belirtmek için sıfır belirtmek için sıfır olmayan değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="29269-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="29269-116">Bu örnek açıkça dönüş değeri olarak ayarlar **true** numaralandırma devam etmek için.</span><span class="sxs-lookup"><span data-stu-id="29269-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="29269-117">Bir temsilci oluşturun ve bu bağımsız değişken olarak geçirin **EnumWindows** işlevi.</span><span class="sxs-lookup"><span data-stu-id="29269-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="29269-118">Platform çağırma temsilcisi tanıdık geri çağırma biçimine otomatik olarak dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="29269-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="29269-119">Geri çağırma işlevi çalışmasını tamamlanmadan önce atık toplayıcı temsilci geri değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="29269-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="29269-120">Parametre olarak bir temsilci geçirmek ya da bir yapı bir alan olarak bulunan bir temsilci geçirmek için çağrı süresi uncollected kalır.</span><span class="sxs-lookup"><span data-stu-id="29269-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="29269-121">Bu nedenle, aşağıdaki numaralandırma örnekte olduğu gibi geri çağırma işlevi çalışmasını çağrı döndürür ve yönetilen çağıran tarafından başka bir eylem gerektiren önce tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="29269-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="29269-122">Eğer, ancak geri çağırma işlevi çağrısı döndükten sonra çağrılabilir, yönetilen arayan geri çağırma işlevi tamamlanana kadar temsilci uncollected kaldığından emin olmak için adımlar atmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="29269-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="29269-123">Çöp toplama önleme hakkında ayrıntılı bilgi için bkz: [birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md) Platform Çağırma ile.</span><span class="sxs-lookup"><span data-stu-id="29269-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29269-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="29269-124">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="29269-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29269-125">See Also</span></span>  
 [<span data-ttu-id="29269-126">Geri arama işlevleri</span><span class="sxs-lookup"><span data-stu-id="29269-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 [<span data-ttu-id="29269-127">DLL işlevini çağırma</span><span class="sxs-lookup"><span data-stu-id="29269-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
