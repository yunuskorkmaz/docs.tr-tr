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
ms.openlocfilehash: 45810390ced8584ea7b37908a9e4af8d3da73f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549856"
---
# <a name="specifying-a-character-set"></a>Karakter Kümesi Belirtme
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan denetimleri dize sıralama ve platform çağırma DLL'de bulur işlev adlarını nasıl belirler. Bu konuda, hem davranışları açıklanmaktadır.  
  
 Bazı API'leri iki dize bağımsız değişkenler almayan işlevleri sürümü dışarı aktar: (ANSI) dar ve geniş (Unicode). Win32 API örneği için aşağıdaki giriş noktası adları içeren **MessageBox** işlevi:  
  
-   **MessageBoxA**  
  
     1-bayt karakter ANSI biçimlendirme, "A" giriş noktası adına göre ayırt sağlar. Çağrılar **MessageBoxA** , Windows 95 ve Windows 98 platformlarında yaygın olarak bulunur, ANSI dizelerini sıralama her zaman biçimlendirme.  
  
-   **MessageBoxW**  
  
     2-bayt karakter Unicode biçimlendirme, "W" giriş noktası adına göre ayırt sağlar. Çağrılar **MessageBoxW** her zaman Windows NT, Windows 2000 ve Windows XP platformlarında yaygın olduğu gibi Unicode biçiminde dizeleri sıralama.  
  
## <a name="string-marshaling-and-name-matching"></a>Dize sıralama ve adı ile eşleşen  
 **CharSet** alan aşağıdaki değerleri kabul eder:  
  
 **CharSet.Ansi** (varsayılan değer)  
  
-   Dize sıralama  
  
     Platform çağırma sıraladığında dizeleri ANSI biçimine yönetilen biçimlerini (Unicode).  
  
-   Ad eşleştirme  
  
     Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır **true**, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.  
  
     Zaman **ExactSpelling** alandır **false**, C++'da varsayılan olarak ve C#, platform çağırma unmangled diğer arar ilk (**MessageBox**), sonra Karıştırılmış adı (**MessageBoxA**) unmangled diğer bulunamaması durumunda. ANSI adı eşleştirme davranışı Unicode adıyla eşleşen davranış farklı olduğuna dikkat edin.  
  
 **DllImport.charset'i**  
  
-   Dize sıralama  
  
     Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizeleri Unicode biçiminde.  
  
-   Ad eşleştirme  
  
     Zaman **ExactSpelling** alandır **true**, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamazsanız başarısız olur.  
  
     Zaman **ExactSpelling** alandır **false**, C++'da varsayılan olarak ve C#, platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), sonra unmangled diğer ad (**MessageBox**) karıştırılmış adı bulunmazsa. Unicode adı eşleştirme davranışı ANSI adıyla eşleşen davranış farklı olduğuna dikkat edin.  
  
 **CharSet.Auto**  
  
-   Platform çağırma arasında ANSI ve Unicode biçimlerini hedef platformunu temel alan çalışma zamanında seçer.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Visual Basic'te bir karakter kümesi belirtme  
 Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her seferinde farklı karakter kümesi davranış. Karakter kümesi davranış ekleyerek Visual Basic'te belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.  
  
 İlk bildirim deyiminde olduğu gibi karakter kümesi anahtar sözcüğü atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ANSI karakter kümesi için varsayılan alan. Örnek ikinci ve üçüncü ifadeler karakter kümesi anahtar sözcüğü ile açıkça belirtin.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a>İçinde bir karakter kümesi belirtme C# ve C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar. Karakter dizesi bağımsız değişkenleri bir yönteme nasıl sıralanması gerektiğini denetimleri ayarlayın. Karakter kümesi belirtmek için aşağıdaki biçimlerden birini kullanın:  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 Aşağıdaki örnek, üç yönetilen tanımını gösterir **MessageBox** işleve atfedilen karakter kümesi belirtmek için. İlk tanımında, atlama tarafından **CharSet** ANSI karakter kümesi için varsayılan alan.  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Platform Çağırma Örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)
- [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
