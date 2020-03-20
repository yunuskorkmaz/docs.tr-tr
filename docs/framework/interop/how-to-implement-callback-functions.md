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
# <a name="how-to-implement-callback-functions"></a>Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama
Aşağıdaki yordam ve örnek, yönetilen bir uygulamanın platform çağrısını kullanarak, her pencere için işlem değerini yerel bilgisayarda nasıl yazdırabileceğini gösterir. Özellikle, yordam ve örnek pencere tutamacının değerini yazdırmak için windows listesi ve yönetilen bir geri arama işlevi (CallBack adlı) üzerinden adım **EnumWindows** işlevini kullanın.  
  
### <a name="to-implement-a-callback-function"></a>Geri arama işlevi uygulamak için  
  
1. Uygulamayla daha ileri gitmeden önce **EnumWindows** işlevinin imzasına bakın. **EnumWindows** aşağıdaki imzaya sahiptir:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Bu işlevin geri arama gerektirdiğine dair bir ipucu **lpEnumFunc** bağımsız değişkeninin varlığıdır. Bir geri çağırma işlevine işaretçi alan bağımsız değişkenler adında **Func** sonekiyle birleştirilmiş **lp** (uzun işaretçi) öneki görmek yaygındır. Win32 işlevleri yle ilgili belgeler için Microsoft Platform SDK'ya bakın.  
  
2. Yönetilen geri arama işlevini oluşturun. Örnek, iki bağımsız değişken `CallBack`**(hwnd** ve **lparam)** alan , adlı bir temsilci türü bildirir. İlk bağımsız değişken, pencerenin tutamacıdır; ikinci bağımsız değişken uygulama tanımlı. Bu sürümde, her iki bağımsız değişken de tamsayılar olmalıdır.  
  
     Geri arama işlevleri genellikle başarıyı belirtmek için sıfır olmayan değerleri ve başarısızlığı belirtmek için sıfır ı döndürür. Bu örnek, numaralandırmaya devam etmek için iade değerini **açıkça true** olarak ayarlar.  
  
3. Bir temsilci oluşturun ve **bunu EnumWindows** işlevine bağımsız değişken olarak geçirin. Platform çağrısı, temsilciyi otomatik olarak tanıdık bir geri arama biçimine dönüştürür.  
  
4. Geri arama işlevi çalışmasını tamamlamadan önce çöp toplayıcının temsilciyi geri almamasını sağlayın. Bir temsilciyi parametre olarak geçtiğinde veya bir yapıda alan olarak bulunan bir temsilciyi geçtiğinde, çağrı süresince toplanmamış kalır. Bu nedenle, aşağıdaki numaralandırma örneğinde olduğu gibi, geri arama işlevi arama dönmeden önce çalışmasını tamamlar ve yönetilen arayan tarafından ek bir eylem gerektirmez.  
  
     Ancak, geri arama işlevi çağrı döndükten sonra çağrılabilirse, yönetilen arayan, geri arama işlevi bitene kadar temsilcinin toplanmamış kalmasını sağlamak için adımlar atmalıdır. Çöp toplamayı önleme hakkında ayrıntılı bilgi için Platform Invoke ile [Interop Marshaling'e](interop-marshaling.md) bakın.  
  
## <a name="example"></a>Örnek  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geri Çağırma İşlevleri](callback-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
