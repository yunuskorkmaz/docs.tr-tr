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
ms.openlocfilehash: 23355e16127b45c26a1d950c6a8b3cc27e265781
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123881"
---
# <a name="how-to-implement-callback-functions"></a>Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama
Aşağıdaki yordam ve örnek, platform çağırma kullanılarak yönetilen bir uygulamanın, yerel bilgisayardaki her bir pencere için tanıtıcı değerini nasıl yazdırabileceğini göstermektedir. Özellikle, yordam ve örnek, pencere tanıtıcısının değerini yazdırmak için Windows listesini ve yönetilen bir geri çağırma işlevini (geri çağırma) adım adım almak için **EnumWindows** işlevini kullanır.  
  
### <a name="to-implement-a-callback-function"></a>Bir geri çağırma işlevi uygulamak için  
  
1. Uygulamayla devam etmeden önce **EnumWindows** işlevinin imzasına bakın. **EnumWindows** aşağıdaki imzaya sahiptir:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Bu işlevin bir geri çağırma gerektirdiğini belirten bir Clue, **Lpenumfunc** bağımsız değişkeninin varlığına sahip olur. Bir geri çağırma işlevine işaretçi alan bağımsız değişkenlerin adında, **LP** (uzun işaretçi) ön ekinin **Func** sonekiyle birleştirilmiş olması yaygındır. Win32 işlevleri hakkındaki belgeler için bkz. Microsoft Platform SDK.  
  
2. Yönetilen geri çağırma işlevini oluşturun. Örnek, iki bağımsız değişken (**HWND** ve **lparam**) alan `CallBack`adlı bir temsilci türü bildirir. İlk bağımsız değişken pencerenin bir tanıtıcıdır; İkinci bağımsız değişken uygulama tanımlı. Bu sürümde, her iki bağımsız değişken de tamsayı olmalıdır.  
  
     Geri çağırma işlevleri, hatayı göstermek için genellikle sıfır dışı değerleri döndürür ve başarıyı gösterir. Bu örnek, numaralandırmaya devam etmek için return değerini açık olarak **true** olarak ayarlar.  
  
3. Bir temsilci oluşturun ve bunu **EnumWindows** işlevine bağımsız değişken olarak geçirin. Platform çağırma, temsilciyi otomatik olarak tanıdık bir geri çağırma biçimine dönüştürür.  
  
4. Çöp toplayıcısının, geri çağırma işlevi işini tamamlamadan önce temsilciyi geri içermediğinden emin olun. Bir temsilciyi parametre olarak geçirdiğinizde veya bir yapıda alan olarak bulunan bir temsilciyi geçirdiğinizde, çağrının süresi boyunca toplanmamış olarak kalır. Bu nedenle, aşağıdaki numaralandırma örneğinde olduğu gibi, geri çağırma işlevi, çağrı döndürülmeden önce çalışmasını tamamlar ve yönetilen çağıran tarafından başka bir eylem gerektirmez.  
  
     Ancak, geri çağırma işlevi çağrı çağrıldıktan sonra çağrılırsa, geri çağırma işlevi bitene kadar, yönetilen çağıran, temsilcinin toplanmamış olarak kalmasını sağlamak için adımları almalıdır. Çöp toplamayı önlemek hakkında ayrıntılı bilgi için bkz. platform çağırma ile [birlikte çalışma hazırlama](interop-marshaling.md) .  
  
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

- [Geri Arama İşlevleri](callback-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
