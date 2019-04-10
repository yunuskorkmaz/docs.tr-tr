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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0936b1dc60bf6ca6dae3b5351b0717929c50876a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214072"
---
# <a name="how-to-implement-callback-functions"></a>Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama
Aşağıdaki yordam ve örnek platformunu kullanarak yönetilen bir uygulamada nasıl çağırma göstermek, her pencere tanıtıcısı değeri yerel bilgisayarda yazdırabilir. Özellikle, yordam ve örnek kullanım **EnumWindows** işlev için windows ve yönetilen bir geri çağırma işlevi (pencere tanıtıcısı değerini yazdırmak için adlandırılmış geri çağırma işlemini) listesinde ilerleyin.  
  
### <a name="to-implement-a-callback-function"></a>Bir geri çağırma işlevini uygulamak için  
  
1.  İmzası bakın **EnumWindows** başka bir uygulama ile geçmeden önce işlevi. **EnumWindows** şu imzaya sahip:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Bu işlev bir geri çağırma gerektiren bir ipucudur varlığını **lpEnumFunc** bağımsız değişken. Yaygın **lp** (uzun işaretçisi) öneki Sunucusu'yla birlikte **Func** soneki adını almak için bir geri arama işlevine bir işaretçi bağımsız değişkenler. Microsoft Platform SDK'sı Win32 işlevlerini ilgili belgeler için bkz.  
  
2.  Yönetilen bir geri çağırma işlevi oluşturun. Örnek adlı bir temsilci türü bildirir `CallBack`, iki bağımsız değişken alır (**hwnd** ve **lparam**). İlk bağımsız değişken penceresinde bir işleyicisidir; İkinci bağımsız değişkeni uygulama tarafından tanımlanır. Bu sürümde, her iki değişken tamsayılar olmalıdır.  
  
     Geri çağırma işlevleri genellikle başarı ve başarısızlık belirtmek için sıfır belirtmek için sıfır olmayan değerler döndürür. Bu örnek açıkça dönüş değeri ayarlar **true** numaralandırma devam etmek için.  
  
3.  Temsilci oluşturmak ve bağımsız değişken olarak geçirin **EnumWindows** işlevi. Platform çağırma temsilci otomatik olarak tanıdık geri çağırma biçimine dönüştürür.  
  
4.  Geri çağırma işlevi, iş tamamlanmadan önce çöp toplayıcı temsilci kazanmıyor emin olun. Bir temsilci bir parametre olarak geçir veya yapısına bir alan olarak yer alan bir temsilci geçirmek, çağrı süresi boyunca uncollected kalır. Bu nedenle, sabit listesi aşağıdaki örnekte olduğu gibi geri çağırma işlevi işini tamamlayıncaya önce çağrı döndürür ve yönetilen çağıran tarafından başka bir işlem gerektirir.  
  
     Eğer, ancak geri çağırma işlevi çağrısı döndürdükten sonra çağrılabilir, yönetilen çağırana geri çağırma işlevi bitene kadar temsilci uncollected kalmasını sağlamak için adımları uygulamanız gerekir. Çöp toplama engelleme hakkında ayrıntılı bilgi için bkz: [birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md) Platform Çağırma ile.  
  
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

- [Geri Çağırma İşlevleri](../../../docs/framework/interop/callback-functions.md)
- [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
