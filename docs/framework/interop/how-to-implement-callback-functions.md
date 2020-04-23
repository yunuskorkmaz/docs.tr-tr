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
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="20bc5-102">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="20bc5-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="20bc5-103">Aşağıdaki yordam ve örnek, platform çağırma kullanılarak yönetilen bir uygulamanın, yerel bilgisayardaki her bir pencere için tanıtıcı değerini nasıl yazdırabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="20bc5-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="20bc5-104">Özellikle, yordam ve örnek, pencere tanıtıcısının değerini yazdırmak için Windows listesini ve yönetilen bir geri çağırma işlevini (geri çağırma) adım adım almak için **EnumWindows** işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="20bc5-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="20bc5-105">Bir geri çağırma işlevi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="20bc5-105">To implement a callback function</span></span>  
  
1. <span data-ttu-id="20bc5-106">Uygulamayla devam etmeden önce **EnumWindows** işlevinin imzasına bakın.</span><span class="sxs-lookup"><span data-stu-id="20bc5-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="20bc5-107">**EnumWindows** aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="20bc5-107">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="20bc5-108">Bu işlevin bir geri çağırma gerektirdiğini belirten bir Clue, **Lpenumfunc** bağımsız değişkeninin varlığına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="20bc5-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="20bc5-109">Bir geri çağırma işlevine işaretçi alan bağımsız değişkenlerin adında, **LP** (uzun işaretçi) ön ekinin **Func** sonekiyle birleştirilmiş olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="20bc5-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="20bc5-110">Win32 işlevleri hakkındaki belgeler için bkz. Microsoft Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="20bc5-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="20bc5-111">Yönetilen geri çağırma işlevini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20bc5-111">Create the managed callback function.</span></span> <span data-ttu-id="20bc5-112">Örnek, iki bağımsız değişken (**HWND** ve `CallBack` **lParam**) alan çağrılan bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="20bc5-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="20bc5-113">İlk bağımsız değişken pencerenin bir tanıtıcıdır; İkinci bağımsız değişken uygulama tanımlı.</span><span class="sxs-lookup"><span data-stu-id="20bc5-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="20bc5-114">Bu sürümde, her iki bağımsız değişken de tamsayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20bc5-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="20bc5-115">Geri çağırma işlevleri, hatayı göstermek için genellikle sıfır dışı değerleri döndürür ve başarıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="20bc5-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="20bc5-116">Bu örnek, numaralandırmaya devam etmek için return değerini açık olarak **true** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="20bc5-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="20bc5-117">Bir temsilci oluşturun ve bunu **EnumWindows** işlevine bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="20bc5-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="20bc5-118">Platform çağırma, temsilciyi otomatik olarak tanıdık bir geri çağırma biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="20bc5-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="20bc5-119">Çöp toplayıcısının, geri çağırma işlevi işini tamamlamadan önce temsilciyi geri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="20bc5-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="20bc5-120">Bir temsilciyi parametre olarak geçirdiğinizde veya bir yapıda alan olarak bulunan bir temsilciyi geçirdiğinizde, çağrının süresi boyunca toplanmamış olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="20bc5-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="20bc5-121">Bu nedenle, aşağıdaki numaralandırma örneğinde olduğu gibi, geri çağırma işlevi, çağrı döndürülmeden önce çalışmasını tamamlar ve yönetilen çağıran tarafından başka bir eylem gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="20bc5-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="20bc5-122">Ancak, geri çağırma işlevi çağrı çağrıldıktan sonra çağrılırsa, geri çağırma işlevi bitene kadar, yönetilen çağıran, temsilcinin toplanmamış olarak kalmasını sağlamak için adımları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="20bc5-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="20bc5-123">Çöp toplamayı önlemek hakkında ayrıntılı bilgi için bkz. platform çağırma ile [birlikte çalışma hazırlama](interop-marshaling.md) .</span><span class="sxs-lookup"><span data-stu-id="20bc5-123">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20bc5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="20bc5-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20bc5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20bc5-125">See also</span></span>

- [<span data-ttu-id="20bc5-126">Geri Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="20bc5-126">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="20bc5-127">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="20bc5-127">Calling a DLL Function</span></span>](calling-a-dll-function.md)
