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
ms.openlocfilehash: 410c8bdb63b56a78dbfa64c21344fdcd6a6656c3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051604"
---
# <a name="specifying-an-entry-point"></a>Giriş Noktası Belirtme
Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar. Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar. Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.  
  
 Bir DLL işlevini yeniden adlandırmak için olası nedenlerin bir listesi aşağıdadır:  
  
- Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için  
  
- Varolan adlandırma standartlarına uymak için  
  
- Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)  
  
- ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için  
  
 Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Visual Basic'te bir İşlevi Yeniden Adlandırma  
 Visual Basic, <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanı ayarlamak için **Declare** deyimindeki **Function** anahtar sözcüğünü kullanır. Aşağıdaki örnek, temel bir bildirimi gösterir.  
  
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
  
## <a name="renaming-a-function-in-c-and-c"></a>C# ve C++'de bir İşlevi Yeniden Adlandırma  
 Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz. Yöntem tanımınızdaki işlevin adı DLL 'deki giriş noktasıyla aynıysa, işlevi **entryPoint** alanı ile açıkça belirlemeniz gerekmez. Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.  
  
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
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [Platform Çağırma Örnekleri](platform-invoke-examples.md)
- [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)
