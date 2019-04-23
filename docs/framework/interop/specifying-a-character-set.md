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
ms.openlocfilehash: 798fcacab5bd74dbd6569a68a3b598c0bb63a0a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087748"
---
# <a name="specifying-a-character-set"></a>Karakter Kümesi Belirtme
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan denetimleri dize sıralama ve platform çağırma DLL'de bulur işlev adlarını nasıl belirler. Bu konuda, hem davranışları açıklanmaktadır.  
  
 Bazı API'leri iki dize bağımsız değişkenler almayan işlevleri sürümü dışarı aktar: (ANSI) dar ve geniş (Unicode). Windows API, örneğin, aşağıdaki giriş noktası adları içerir **MessageBox** işlevi:  
  
-   **MessageBoxA**  
  
     1-bayt karakter ANSI biçimlendirme, "A" giriş noktası adına göre ayırt sağlar. Çağrılar **MessageBoxA** her zaman dizeleri ANSI biçimde hazırlama.  
  
-   **MessageBoxW**  
  
     2-bayt karakter Unicode biçimlendirme, "W" giriş noktası adına göre ayırt sağlar. Çağrılar **MessageBoxW** her zaman dizeleri Unicode biçiminde hazırlama.  
  
## <a name="string-marshaling-and-name-matching"></a>Dize sıralama ve adı ile eşleşen  
 `CharSet` Alan aşağıdaki değerleri kabul eder:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi> (varsayılan değer)  
  
-   Dize sıralama  
  
     Platform çağırma sıraladığında dizeleri ANSI biçimine yönetilen biçimlerini (Unicode).  
  
-   Ad eşleştirme  
  
     Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır `true`, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.  
  
     Zaman `ExactSpelling` alandır `false`, C++'da varsayılan olarak ve C#, platform çağırma unmangled diğer arar ilk (**MessageBox**), ardından karıştırılmış adı (**MessageBoxA**) unmangled diğer bulunamaması durumunda. ANSI adı eşleştirme davranışı Unicode adıyla eşleşen davranış farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   Dize sıralama  
  
     Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizeleri Unicode biçiminde.  
  
-   Ad eşleştirme  
  
     Zaman `ExactSpelling` alandır `true`, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamazsanız başarısız olur.  
  
     Zaman `ExactSpelling` alandır `false`, C++'da varsayılan olarak ve C#, platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), ardından unmangled diğer ad (**MessageBox**) karıştırılmış adı bulunmazsa. Unicode adı eşleştirme davranışı ANSI adıyla eşleşen davranış farklı olduğuna dikkat edin.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   Platform çağırma arasında ANSI ve Unicode biçimlerini hedef platformunu temel alan çalışma zamanında seçer.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Visual Basic'te bir karakter kümesi belirtme  
 Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her seferinde farklı karakter kümesi davranış. Karakter kümesi davranış ekleyerek Visual Basic'te belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.  
  
 İlk bildirim deyiminde olduğu gibi karakter kümesi anahtar sözcüğü atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ANSI karakter kümesi için varsayılan alan. Örnek ikinci ve üçüncü ifadeler karakter kümesi anahtar sözcüğü ile açıkça belirtin.  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a>İçinde bir karakter kümesi belirtme C# ve C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar. Karakter dizesi bağımsız değişkenleri bir yönteme nasıl sıralanması gerektiğini denetimleri ayarlayın. Karakter kümesi belirtmek için aşağıdaki biçimlerden birini kullanın:  
  
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
  
 Aşağıdaki örnek, üç yönetilen tanımını gösterir **MessageBox** işleve atfedilen karakter kümesi belirtmek için. İlk tanımında, atlama tarafından `CharSet` ANSI karakter kümesi için varsayılan alan.  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
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
- [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Platform Çağırma Örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)
- [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
