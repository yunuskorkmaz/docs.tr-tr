---
title: "Karakter Kümesi Belirtme"
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
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb2ae519b4a3d52c590f050ba728286898373ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-a-character-set"></a>Karakter Kümesi Belirtme
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alanı denetimleri dize sıralama ve nasıl platform çağırma bulur işlevi DLL adlarında belirler. Bu konuda iki davranışları açıklanmaktadır.  
  
 Bazı API'leri iki sürümü dize bağımsız değişkenler almayan işlevleri dışarı aktarma: dar (ANSI) ve geniş (Unicode). Win32 API örneği için aşağıdaki giriş noktası adları içeren **MessageBox** işlevi:  
  
-   **MessageBoxA**  
  
     1-bayt karakter ANSI biçimlendirme, giriş noktası adının sonuna bir "A" ayırt edilen sağlar. Çağrılar **MessageBoxA** , Windows 95 ve Windows 98 platformlarında ortak olduğu gibi ANSI dizelerini sıralama her zaman biçimlendirme.  
  
-   **MessageBoxW**  
  
     2-bayt karakter Unicode biçimlendirme, "giriş noktası adına eklenen W" ayırt edilen sağlar. Çağrılar **MessageBoxW** her zaman Unicode biçiminde Windows NT, Windows 2000 ve Windows XP platformlarda ortak olarak dizeleri sıralama.  
  
## <a name="string-marshaling-and-name-matching"></a>Dize sıralama ve adıyla eşleşen  
 **CharSet** alan aşağıdaki değerleri kabul eder:  
  
 **CharSet.Ansi** (varsayılan değer)  
  
-   Hazırlama dize  
  
     Platform çağırma yönetilen biçimlerini (Unicode) sıraladığında dizelerden ANSI biçimine.  
  
-   Ad eşleştirme  
  
     Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır **true**, varsayılan olarak olarak [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.  
  
     Zaman **ExactSpelling** alandır **false**, C++ ve C# varsayılan olarak olduğu gibi platform çağırma unmangled arar alias ilk (**MessageBox**), ardından Karıştırılmış Ad ( **MessageBoxA**) unmangled diğer bulunmazsa. ANSI adıyla eşleşen davranış Unicode adıyla eşleşen davranışından farklıdır dikkat edin.  
  
 **CharSet.Unicode**  
  
-   Hazırlama dize  
  
     Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizelerden Unicode biçimine.  
  
-   Ad eşleştirme  
  
     Zaman **ExactSpelling** alandır **true**, varsayılan olarak olarak [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar. Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.  
  
     Zaman **ExactSpelling** alandır **false**, C++ ve C# varsayılan olarak olduğu gibi platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), ardından unmangled diğer adı (**MessageBox**) karıştırılmış adı bulunmazsa. Unicode adıyla eşleşen davranış ANSI adıyla eşleşen davranışından farklıdır dikkat edin.  
  
 **CharSet.Auto**  
  
-   Platform çağırma hedef platformu temel alarak ANSI veya Unicode biçimleri çalışma zamanında arasında seçer.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Visual Basic'te bir karakter kümesi belirtme  
 Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her zaman farklı karakter kümesi davranışına sahip. Ekleyerek Visual Basic'te karakter kümesi davranış belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.  
  
 Karakter kümesi anahtar sözcüğü ilk bildirimi deyiminde gerçekleştirilir gibi atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan ANSI karakter kümesini varsayılanlara. Örnek ikinci ve üçüncü deyimlerinde açıkça karakter olan bir anahtar sözcük kümesi belirtin.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>C# ve C++ karakter kümesi belirtme  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar. Dize bağımsız değişkeni bir yönteme nasıl sıralanmalıdır denetimleri karakter kümesi. Karakter kümesini belirtmek için aşağıdaki biçimlerden birini kullanın:  
  
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
  
 Aşağıdaki örnekte, üç yönetilen tanımlarını gösterir **MessageBox** işlevi öznitelikli bir karakter kümesini belirtmek için. Kendi atlandığını tarafından ilk tanımında **CharSet** alan ANSI karakter kümesini varsayılanlara.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Platform Çağırma Örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
