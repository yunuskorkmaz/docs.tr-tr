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
ms.openlocfilehash: 1016a0c63a85919764271e01771ff8192341725c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="175dc-102">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="175dc-102">Specifying a Character Set</span></span>
<span data-ttu-id="175dc-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alanı denetimleri dize sıralama ve nasıl platform çağırma bulur işlevi DLL adlarında belirler.</span><span class="sxs-lookup"><span data-stu-id="175dc-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="175dc-104">Bu konuda iki davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="175dc-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="175dc-105">Bazı API'leri iki sürümü dize bağımsız değişkenler almayan işlevleri dışarı aktarma: dar (ANSI) ve geniş (Unicode).</span><span class="sxs-lookup"><span data-stu-id="175dc-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="175dc-106">Win32 API örneği için aşağıdaki giriş noktası adları içeren **MessageBox** işlevi:</span><span class="sxs-lookup"><span data-stu-id="175dc-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="175dc-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="175dc-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="175dc-108">1-bayt karakter ANSI biçimlendirme, giriş noktası adının sonuna bir "A" ayırt edilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="175dc-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="175dc-109">Çağrılar **MessageBoxA** , Windows 95 ve Windows 98 platformlarında ortak olduğu gibi ANSI dizelerini sıralama her zaman biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="175dc-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="175dc-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="175dc-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="175dc-111">2-bayt karakter Unicode biçimlendirme, "giriş noktası adına eklenen W" ayırt edilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="175dc-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="175dc-112">Çağrılar **MessageBoxW** her zaman Unicode biçiminde Windows NT, Windows 2000 ve Windows XP platformlarda ortak olarak dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="175dc-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="175dc-113">Dize sıralama ve adıyla eşleşen</span><span class="sxs-lookup"><span data-stu-id="175dc-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="175dc-114">**CharSet** alan aşağıdaki değerleri kabul eder:</span><span class="sxs-lookup"><span data-stu-id="175dc-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="175dc-115">**CharSet.Ansi** (varsayılan değer)</span><span class="sxs-lookup"><span data-stu-id="175dc-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="175dc-116">Hazırlama dize</span><span class="sxs-lookup"><span data-stu-id="175dc-116">String marshaling</span></span>  
  
     <span data-ttu-id="175dc-117">Platform çağırma yönetilen biçimlerini (Unicode) sıraladığında dizelerden ANSI biçimine.</span><span class="sxs-lookup"><span data-stu-id="175dc-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="175dc-118">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="175dc-118">Name matching</span></span>  
  
     <span data-ttu-id="175dc-119">Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır **true**, varsayılan olarak olarak [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="175dc-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="175dc-120">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="175dc-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="175dc-121">Zaman **ExactSpelling** alandır **false**, C++ ve C# varsayılan olarak olduğu gibi platform çağırma unmangled arar alias ilk (**MessageBox**), ardından Karıştırılmış Ad ( **MessageBoxA**) unmangled diğer bulunmazsa.</span><span class="sxs-lookup"><span data-stu-id="175dc-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="175dc-122">ANSI adıyla eşleşen davranış Unicode adıyla eşleşen davranışından farklıdır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="175dc-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="175dc-123">**CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="175dc-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="175dc-124">Hazırlama dize</span><span class="sxs-lookup"><span data-stu-id="175dc-124">String marshaling</span></span>  
  
     <span data-ttu-id="175dc-125">Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizelerden Unicode biçimine.</span><span class="sxs-lookup"><span data-stu-id="175dc-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="175dc-126">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="175dc-126">Name matching</span></span>  
  
     <span data-ttu-id="175dc-127">Zaman **ExactSpelling** alandır **true**, varsayılan olarak olarak [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="175dc-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="175dc-128">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="175dc-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="175dc-129">Zaman **ExactSpelling** alandır **false**, C++ ve C# varsayılan olarak olduğu gibi platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), ardından unmangled diğer adı (**MessageBox**) karıştırılmış adı bulunmazsa.</span><span class="sxs-lookup"><span data-stu-id="175dc-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="175dc-130">Unicode adıyla eşleşen davranış ANSI adıyla eşleşen davranışından farklıdır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="175dc-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="175dc-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="175dc-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="175dc-132">Platform çağırma hedef platformu temel alarak ANSI veya Unicode biçimleri çalışma zamanında arasında seçer.</span><span class="sxs-lookup"><span data-stu-id="175dc-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="175dc-133">Visual Basic'te bir karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="175dc-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="175dc-134">Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her zaman farklı karakter kümesi davranışına sahip.</span><span class="sxs-lookup"><span data-stu-id="175dc-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="175dc-135">Ekleyerek Visual Basic'te karakter kümesi davranış belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="175dc-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="175dc-136">Karakter kümesi anahtar sözcüğü ilk bildirimi deyiminde gerçekleştirilir gibi atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan ANSI karakter kümesini varsayılanlara.</span><span class="sxs-lookup"><span data-stu-id="175dc-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="175dc-137">Örnek ikinci ve üçüncü deyimlerinde açıkça karakter olan bir anahtar sözcük kümesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="175dc-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="175dc-138">C# ve C++ karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="175dc-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="175dc-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="175dc-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="175dc-140">Dize bağımsız değişkeni bir yönteme nasıl sıralanmalıdır denetimleri karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="175dc-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="175dc-141">Karakter kümesini belirtmek için aşağıdaki biçimlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="175dc-141">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="175dc-142">Aşağıdaki örnekte, üç yönetilen tanımlarını gösterir **MessageBox** işlevi öznitelikli bir karakter kümesini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="175dc-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="175dc-143">Kendi atlandığını tarafından ilk tanımında **CharSet** alan ANSI karakter kümesini varsayılanlara.</span><span class="sxs-lookup"><span data-stu-id="175dc-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="175dc-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="175dc-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="175dc-145">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="175dc-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="175dc-146">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="175dc-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="175dc-147">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="175dc-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
