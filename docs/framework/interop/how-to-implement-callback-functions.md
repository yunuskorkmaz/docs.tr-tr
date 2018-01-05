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
ms.workload: dotnet
ms.openlocfilehash: 819861f9bf13f9af3fab7a1ea7ffc697c1d98926
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-callback-functions"></a>Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama
Aşağıdaki yordamı ve örnek platformu kullanılarak yönetilen bir uygulamanın nasıl çağırma göstermek, her pencere tanıtıcısı değeri yerel bilgisayarda yazdırabilirsiniz. Özellikle, yordam ve örnek kullanım **EnumWindows** işlev adıma windows ve yönetilen geri çağırma işlevi adlandırılmış (bir pencere tanıtıcının değerini yazdırmak için geri çağırma) listesi aracılığıyla.  
  
### <a name="to-implement-a-callback-function"></a>Bir geri çağırma işlevini uygulamak için  
  
1.  İmza için bakabilir **EnumWindows** başka bir uygulama ile geçmeden önce işlevi. **EnumWindows** aşağıdaki imzası vardır:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Bu işlev bir geri çağırma gerektiren bir ipucu olan varlığını **lpEnumFunc** bağımsız değişkeni. Yaygın **lp** (uzun işaretçisi) öneki birlikte **Func** bir geri çağırma işlevini gösteren bir işaretçi ele bağımsız değişken adına soneki. Win32 işlevleri ile ilgili belgeler için Microsoft Platformu SDK'sı bakın.  
  
2.  Yönetilen geri çağırma işlevi oluşturun. Örnek olarak adlandırılan bir temsilci türü bildirir `CallBack`, iki bağımsız değişkeni alır (**hwnd** ve **lparam**). İlk bağımsız değişkeni bir tanıtıcı penceresine değil; İkinci bağımsız değişkeni uygulama tanımlanır. Bu sürümde, her iki değişken tamsayı olması gerekir.  
  
     Geri arama işlevleri genellikle başarı ve başarısızlık belirtmek için sıfır belirtmek için sıfır olmayan değerler döndürür. Bu örnek açıkça dönüş değeri olarak ayarlar **true** numaralandırma devam etmek için.  
  
3.  Bir temsilci oluşturun ve bu bağımsız değişken olarak geçirin **EnumWindows** işlevi. Platform çağırma temsilcisi tanıdık geri çağırma biçimine otomatik olarak dönüştürür.  
  
4.  Geri çağırma işlevi çalışmasını tamamlanmadan önce atık toplayıcı temsilci geri değil emin olun. Parametre olarak bir temsilci geçirmek ya da bir yapı bir alan olarak bulunan bir temsilci geçirmek için çağrı süresi uncollected kalır. Bu nedenle, aşağıdaki numaralandırma örnekte olduğu gibi geri çağırma işlevi çalışmasını çağrı döndürür ve yönetilen çağıran tarafından başka bir eylem gerektiren önce tamamlanır.  
  
     Eğer, ancak geri çağırma işlevi çağrısı döndükten sonra çağrılabilir, yönetilen arayan geri çağırma işlevi tamamlanana kadar temsilci uncollected kaldığından emin olmak için adımlar atmanız gerekir. Çöp toplama önleme hakkında ayrıntılı bilgi için bkz: [birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md) Platform Çağırma ile.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geri Arama İşlevleri](../../../docs/framework/interop/callback-functions.md)  
 [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
