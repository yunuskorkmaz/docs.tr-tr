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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ee68d0da3b7f23d4de0192da076ef6f71d6d222
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051628"
---
# <a name="specifying-a-character-set"></a>Karakter Kümesi Belirtme
Alan <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> , dize sıralamasını denetler ve platform çağırma işlevinin bir dll 'de işlev adlarını bulmasını belirler. Bu konuda her iki davranış de açıklanmaktadır.  
  
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
  
     <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> Alan,VisualBasicvarsayılanolarakolduğunda,platformInvokeyalnızcabelirttiğiniz`true`ad için arama yapar. Örneğin, **MessageBox**belirtirseniz, platform çağrısı, **MessageBox** için arama yapar ve tam yazımı bulamıyorsa başarısız olur.  
  
     C#Alanı, ve ' de C++ varsayılan olarak olduğu gibi olduğunda, platform Invoke önce unkarışmış diğer ad (MessageBox), sonra da unkarıştırılmış diğer ad bulunamazsa karıştırılmış adı (MessageBoxA) arar. `false` `ExactSpelling` ANSI ad eşleştirme davranışının Unicode ad eşleştirme davranışından farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Dize sıralama  
  
     Platform çağrısı, dizeleri yönetilen biçiminden (Unicode) Unicode biçimine kopyalar.  
  
- Ad eşleştirme  
  
     `ExactSpelling` Alan,VisualBasicvarsayılanolarakolduğunda,platformInvokeyalnızcabelirttiğiniz`true`ad için arama yapar. Örneğin, **MessageBox**belirtirseniz, Platform **çağırın ve tam** yazım bulamazsa başarısız olur.  
  
     C#Alanı, ve ' de C++ varsayılan olarak olduğu gibi, platform Invoke önce karışmış adı arar (MessageBoxW), daha sonra karıştırılmış ad bulunamazsa, unkarıştırılmış diğer ad (MessageBox). `false` `ExactSpelling` Unicode ad eşleştirme davranışının ANSI ad eşleştirme davranışından farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Platform çağırma, hedef platforma bağlı olarak çalışma zamanında ANSI ve Unicode biçimleri arasında seçer.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Visual Basic bir karakter kümesi belirtme  
 Aşağıdaki örnek, her seferinde farklı karakter kümesi davranışına sahip olan **MessageBox** işlevini üç kez bildirir. Bildirim bildirimine **Ansi**, **UNICODE**veya **Auto** anahtar sözcüğünü ekleyerek Visual Basic karakter kümesi davranışını belirtebilirsiniz.  
  
 Karakter kümesi anahtar sözcüğünü atlarsanız, ilk bildirim ifadesinde <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> yapıldığı gibi, alan varsayılan olarak ANSI karakter kümesi olur. Örnekteki ikinci ve üçüncü deyimler, anahtar sözcüğü olan bir karakter kümesini açıkça belirtir.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Ve ' de C# bir karakter kümesi belirtmeC++  
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
  
 Aşağıdaki örnek, bir karakter kümesi belirtmeye yönelik **MessageBox** işlevinin üç Yönetilen tanımını gösterir. İlk tanımda, atlanarak `CharSet` , alan varsayılan olarak ANSI karakter kümesi olur.  
  
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
- [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)
