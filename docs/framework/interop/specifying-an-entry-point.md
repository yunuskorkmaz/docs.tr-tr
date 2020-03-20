---
title: Giriş Noktası Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: c5f8f735dd3e8c359f88044a532c29303237acc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181306"
---
# <a name="specifying-an-entry-point"></a>Giriş Noktası Belirtme

Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar. Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar. Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.  
  
 Aşağıda, Bir DLL işlevini yeniden adlandırmak için olası nedenlerin bir listesi vetir:  
  
- Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için  
  
- Varolan adlandırma standartlarına uymak için  
  
- Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)  
  
- ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için  
  
 Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Visual Basic'te bir İşlevi Yeniden Adlandırma  

Visual Basic, alanı ayarlamak için **Bildiriyi** <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> beyan etme deyimindeki **İşlev** anahtar sözcük'üne kullanır. Aşağıdaki örnek, temel bir bildirimi gösterir.  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
Aşağıdaki örnekte gösterildiği gibi, tanımınıza **Alias** anahtar sözcüğünüzü ekleyerek **MessageBox** giriş noktasını **MsgBox** ile değiştirebilirsiniz. Her iki örnekte de **Otomatik** anahtar kelime, giriş noktasının karakter kümesi sürümünü belirtme gereksinimini ortadan kaldırır. Karakter kümesi seçme hakkında daha fazla bilgi için [bkz.](specifying-a-character-set.md)  
  
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
 Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz. Yöntem tanımınızdaki işlevin adı DLL'deki giriş noktasıyla aynıysa, İşlevin **EntryPoint** alanıyla açıkça tanımlanması gerekmez. Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.  
  
 Aşağıdaki örnek, **EntryPoint** alanını kullanarak **MessageBoxA'nın** kodunuzda **MsgBox** ile nasıl değiştirilmeye devam edilebildiğini gösterir.  
  
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
- [Platform Çağırma ile Veri Sıralama](marshaling-data-with-platform-invoke.md)
