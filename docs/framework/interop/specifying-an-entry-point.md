---
title: Giriş Noktası Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c278eca421020bea4f36f87eb6c8a9a8ba7d2a43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658292"
---
# <a name="specifying-an-entry-point"></a>Giriş Noktası Belirtme
Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar. Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar. Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.  
  
 Bir DLL işlevini yeniden adlandırmak için olası nedenlerin bir listesi aşağıdadır:  
  
-   Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için  
  
-   Varolan adlandırma standartlarına uymak için  
  
-   Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)  
  
-   ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için  
  
 Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Visual Basic'te bir İşlevi Yeniden Adlandırma  
 Visual Basic kullanan **işlevi** anahtar sözcüğünü **Declare** ayarlamak için ifade <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alan. Aşağıdaki örnek, temel bir bildirimi gösterir.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 Değiştirebilirsiniz **MessageBox** giriş noktasıyla **MsgBox** ekleyerek **diğer** aşağıdaki örnekte gösterildiği gibi tanımınızı, anahtar sözcük. Her iki örnek **otomatik** anahtar sözcüğü giriş noktasının karakter kümesi sürümünü belirtme ihtiyacını ortadan kaldırır. Bir karakter seçme hakkında daha fazla bilgi için bkz: [bir karakter kümesi belirtme](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a>C# ve C++'de bir İşlevi Yeniden Adlandırma  
 Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz. Yöntem tanımınızdaki işlevin adı giriş noktasıyla aynıysa DLL'deki işlevi açıkça tanımlamak gerekmez **EntryPoint** alan. Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.  
  
 Aşağıdaki örnek nasıl değiştirileceğini gösterir **MessageBoxA** ile **MsgBox** kullanarak kodunuzda **EntryPoint** alan.  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Platform Çağırma Örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)
- [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
