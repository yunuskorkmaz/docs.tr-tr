---
title: 'Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: b7aae1e70ac736d60bed1e79291235db1c220281
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181409"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="26a03-102">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="26a03-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="26a03-103">Aşağıdaki yordam ve örnek, yönetilen bir uygulamanın platform çağrısını kullanarak, her pencere için işlem değerini yerel bilgisayarda nasıl yazdırabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a03-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="26a03-104">Özellikle, yordam ve örnek pencere tutamacının değerini yazdırmak için windows listesi ve yönetilen bir geri arama işlevi (CallBack adlı) üzerinden adım **EnumWindows** işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="26a03-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="26a03-105">Geri arama işlevi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="26a03-105">To implement a callback function</span></span>  
  
1. <span data-ttu-id="26a03-106">Uygulamayla daha ileri gitmeden önce **EnumWindows** işlevinin imzasına bakın.</span><span class="sxs-lookup"><span data-stu-id="26a03-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="26a03-107">**EnumWindows** aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="26a03-107">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="26a03-108">Bu işlevin geri arama gerektirdiğine dair bir ipucu **lpEnumFunc** bağımsız değişkeninin varlığıdır.</span><span class="sxs-lookup"><span data-stu-id="26a03-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="26a03-109">Bir geri çağırma işlevine işaretçi alan bağımsız değişkenler adında **Func** sonekiyle birleştirilmiş **lp** (uzun işaretçi) öneki görmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="26a03-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="26a03-110">Win32 işlevleri yle ilgili belgeler için Microsoft Platform SDK'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="26a03-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="26a03-111">Yönetilen geri arama işlevini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="26a03-111">Create the managed callback function.</span></span> <span data-ttu-id="26a03-112">Örnek, iki bağımsız değişken `CallBack`**(hwnd** ve **lparam)** alan , adlı bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="26a03-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="26a03-113">İlk bağımsız değişken, pencerenin tutamacıdır; ikinci bağımsız değişken uygulama tanımlı.</span><span class="sxs-lookup"><span data-stu-id="26a03-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="26a03-114">Bu sürümde, her iki bağımsız değişken de tamsayılar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="26a03-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="26a03-115">Geri arama işlevleri genellikle başarıyı belirtmek için sıfır olmayan değerleri ve başarısızlığı belirtmek için sıfır ı döndürür.</span><span class="sxs-lookup"><span data-stu-id="26a03-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="26a03-116">Bu örnek, numaralandırmaya devam etmek için iade değerini **açıkça true** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26a03-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="26a03-117">Bir temsilci oluşturun ve **bunu EnumWindows** işlevine bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="26a03-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="26a03-118">Platform çağrısı, temsilciyi otomatik olarak tanıdık bir geri arama biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="26a03-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="26a03-119">Geri arama işlevi çalışmasını tamamlamadan önce çöp toplayıcının temsilciyi geri almamasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="26a03-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="26a03-120">Bir temsilciyi parametre olarak geçtiğinde veya bir yapıda alan olarak bulunan bir temsilciyi geçtiğinde, çağrı süresince toplanmamış kalır.</span><span class="sxs-lookup"><span data-stu-id="26a03-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="26a03-121">Bu nedenle, aşağıdaki numaralandırma örneğinde olduğu gibi, geri arama işlevi arama dönmeden önce çalışmasını tamamlar ve yönetilen arayan tarafından ek bir eylem gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="26a03-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="26a03-122">Ancak, geri arama işlevi çağrı döndükten sonra çağrılabilirse, yönetilen arayan, geri arama işlevi bitene kadar temsilcinin toplanmamış kalmasını sağlamak için adımlar atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="26a03-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="26a03-123">Çöp toplamayı önleme hakkında ayrıntılı bilgi için Platform Invoke ile [Interop Marshaling'e](interop-marshaling.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="26a03-123">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26a03-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="26a03-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26a03-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26a03-125">See also</span></span>

- [<span data-ttu-id="26a03-126">Geri Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="26a03-126">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="26a03-127">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="26a03-127">Calling a DLL Function</span></span>](calling-a-dll-function.md)
