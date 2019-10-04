---
title: Giriş noktası belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5449b4fa77ba99a18595077081089e80bd32df
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833615"
---
# <a name="specifying-an-entry-point"></a>Giriş noktası belirtme

Bir giriş noktası, bir DLL içindeki bir işlevin konumunu tanımlar. Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıralı giriş noktası, bu işlevi birlikte çalışma sınırları genelinde tanımlar. Ayrıca, giriş noktasını farklı bir adla eşleyebilir ve işlevi etkin bir şekilde yeniden adlandırmanız gerekir.  
  
 Bir DLL işlevini yeniden adlandırmak için olası nedenlerinin bir listesi aşağıda verilmiştir:  
  
- Büyük/küçük harfe duyarlı API işlev adlarını kullanmaktan kaçınmak için  
  
- Mevcut adlandırma standartlarıyla uyum sağlamak için  
  
- Farklı veri türleri alan işlevlere (aynı DLL işlevinin birden çok sürümünü bildirerek) uyum sağlamak için  
  
- ANSI ve Unicode sürümlerini içeren API 'Leri kullanmayı kolaylaştırmak için  
  
 Bu konu başlığı altında, Yönetilen koddaki bir DLL işlevinin nasıl yeniden adlandırılacağı gösterilmektedir.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Visual Basic bir Işlevi yeniden adlandırma  
 
Visual Basic, <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını ayarlamak için **Declare** deyimindeki **Function** anahtar sözcüğünü kullanır. Aşağıdaki örnek, temel bir bildirimi gösterir.  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
Aşağıdaki örnekte gösterildiği gibi, tanımınıza **diğer ad** anahtar sözcüğünü ekleyerek **MessageBox** giriş noktasını **MsgBox** ile değiştirebilirsiniz. Her iki örnekte de **Auto** anahtar sözcüğü, giriş noktasının karakter kümesi sürümünü belirtme gereksinimini ortadan kaldırır. Bir karakter kümesi seçme hakkında daha fazla bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>Ve içinde C# bir işlevi yeniden adlandırmaC++  
 Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz. Yöntem tanımınızdaki işlevin adı DLL 'deki giriş noktasıyla aynıysa, işlevi **entryPoint** alanı ile açıkça belirlemeniz gerekmez. Aksi takdirde, bir ad veya sıra belirtmek için aşağıdaki öznitelik formlarından birini kullanın:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Numara işareti (#) ile bir sıra öneki yapmanız gerektiğini unutmayın.  
  
 Aşağıdaki örnek, **giriş noktası** alanını kullanarak kodunuzda bir **MsgBox** ile **MessageBoxA** 'nın nasıl değiştirileceğini gösterir.  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen kodda prototipler oluşturma](creating-prototypes-in-managed-code.md)
- [Platform çağırma örnekleri](platform-invoke-examples.md)
- [Platform çağırma ile verileri sıralama](marshaling-data-with-platform-invoke.md)
