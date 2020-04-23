---
title: Karakter Kümesi Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 0db1cd8d75b45f6d718168793c873e5867028269
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125175"
---
# <a name="specifying-a-character-set"></a>Karakter Kümesi Belirtme
Alan <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> , dize sıralamasını denetler ve platform çağırma IŞLEVININ bir dll 'de işlev adlarını bulmasını belirler. Bu konuda her iki davranış de açıklanmaktadır.  
  
 Bazı API 'Ler dize bağımsız değişkenleri alan işlevlerin iki sürümünü dışarı aktarır: dar (ANSI) ve geniş (Unicode). Örneğin, Windows API 'SI, **MessageBox** işlevi için aşağıdaki giriş noktası adlarını içerir:  
  
- **MessageBoxA**  
  
     Giriş noktası adına bir "A" eklenerek ayırt edilen 1 baytlık karakter ANSI biçimlendirmesi sağlar. Her zaman ANSI biçimindeki **MessageBoxA** çağrısı dizeleri.  
  
- **MessageBoxW**  
  
     Giriş noktası adına bir "W" ile ayırt edilen 2 baytlık karakter Unicode biçimlendirmesi sağlar. **MessageBoxW** çağrıları her zaman Unicode biçiminde dizeleri sıralama.  
  
## <a name="string-marshaling-and-name-matching"></a>Dize hazırlama ve ad eşleştirme  
 `CharSet` Alan, aşağıdaki değerleri kabul eder:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi>(varsayılan değer)  
  
- Dize sıralama  
  
     Platform, yönetilen biçimindeki (Unicode) dizeleri ANSI biçimine göre sıralamalarını çağırır.  
  
- Ad eşleştirme  
  
     <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> Alan `true`, Visual Basic varsayılan olarak olduğunda, platform Invoke yalnızca belirttiğiniz ad için arama yapar. Örneğin, **MessageBox**belirtirseniz, platform çağrısı, **MessageBox** için arama yapar ve tam yazımı bulamıyorsa başarısız olur.  
  
     `ExactSpelling` Alan `false`, C++ ve C# ' de varsayılan olarak olduğu gibi, platform Invoke First Unkarışmış diğer ad (**MessageBox**), daha sonra da unkarıştırılmış diğer ad bulunamazsa karıştırılmış adı (**MessageBoxA**) arar. ANSI ad eşleştirme davranışının Unicode ad eşleştirme davranışından farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Dize sıralama  
  
     Platform çağrısı, dizeleri yönetilen biçiminden (Unicode) Unicode biçimine kopyalar.  
  
- Ad eşleştirme  
  
     `ExactSpelling` Alan `true`, Visual Basic varsayılan olarak olduğunda, platform Invoke yalnızca belirttiğiniz ad için arama yapar. Örneğin, **MessageBox**belirtirseniz, Platform **çağırın ve tam** yazım bulamazsa başarısız olur.  
  
     `ExactSpelling` Alan `false`, C++ ve C# ' de varsayılan olarak olduğu gibi, platform Invoke önce karışmış adı arar (**MessageBoxW**), ardından karışmış ad bulunamazsa, unkarıştırılmış diğer ad (**MessageBox**). Unicode ad eşleştirme davranışının ANSI ad eşleştirme davranışından farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Platform çağırma, hedef platforma bağlı olarak çalışma zamanında ANSI ve Unicode biçimleri arasında seçer.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Visual Basic bir karakter kümesi belirtme  
 Aşağıdaki örnek, her seferinde farklı karakter kümesi davranışına sahip olan **MessageBox** işlevini üç kez bildirir. Bildirim bildirimine **Ansi**, **UNICODE**veya **Auto** anahtar sözcüğünü ekleyerek Visual Basic karakter kümesi davranışını belirtebilirsiniz.  
  
 Karakter kümesi anahtar sözcüğünü atlarsanız, ilk bildirim ifadesinde yapıldığı gibi, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan varsayılan olarak ANSI karakter kümesi olur. Örnekteki ikinci ve üçüncü deyimler, anahtar sözcüğü olan bir karakter kümesini açıkça belirtir.  
  
```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a>C# ve C++ içinde bir karakter kümesi belirtme  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan, temel alınan karakter kümesini ANSI veya Unicode olarak tanımlar. Karakter kümesi bir yönteme dize bağımsız değişkenlerinin nasıl sıralanması gerektiğini denetler. Karakter kümesini belirtmek için aşağıdaki formlardan birini kullanın:  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 Aşağıdaki örnek, bir karakter kümesi belirtmeye yönelik **MessageBox** işlevinin üç Yönetilen tanımını gösterir. İlk tanımda, atlanarak, `CharSet` alan varsayılan olarak ANSI karakter kümesi olur.  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [Platform Çağırma Örnekleri](platform-invoke-examples.md)
- [Platform Çağırma ile Veri Sıralama](marshaling-data-with-platform-invoke.md)
