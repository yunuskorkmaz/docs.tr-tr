---
title: "Giriş Noktası Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7406e256acaea0c535c222386c529c4087bbdc6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 Visual Basic kullanan **işlevi** anahtar sözcük **Declare** ayarlamak için ifade <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alan. Aşağıdaki örnek, temel bir bildirimi gösterir.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 Değiştirebileceğiniz **MessageBox** giriş noktasıyla **MsgBox** ekleyerek **diğer** tanımınızı, aşağıdaki örnekte gösterildiği gibi bir anahtar sözcük. Her iki örneklerde **otomatik** anahtar sözcüğü Giriş noktası karakter kümesi sürümünü belirtme ihtiyacını ortadan kaldırır. Bir karakter seçme hakkında daha fazla bilgi için bkz: [karakter kümesini belirtme](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a>C# ve C++'de bir İşlevi Yeniden Adlandırma  
 Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz. Adı yöntemi tanımınızı işlevi, giriş noktası ile aynı ise DLL'de açıkça işleviyle tanımlamak gerekmez **EntryPoint** alan. Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.  
  
 Aşağıdaki örnekte nasıl değiştirileceğini göstermektedir **MessageBoxA** ile **MsgBox** kullanarak kodunuzda **EntryPoint** alan.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Platform çağırma örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
