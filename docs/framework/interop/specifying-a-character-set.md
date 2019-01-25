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
# <a name="specifying-a-character-set"></a><span data-ttu-id="68d75-102">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="68d75-102">Specifying a Character Set</span></span>
<span data-ttu-id="68d75-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan denetimleri dize sıralama ve platform çağırma DLL'de bulur işlev adlarını nasıl belirler.</span><span class="sxs-lookup"><span data-stu-id="68d75-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="68d75-104">Bu konuda, hem davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68d75-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="68d75-105">Bazı API'leri iki dize bağımsız değişkenler almayan işlevleri sürümü dışarı aktar: (ANSI) dar ve geniş (Unicode).</span><span class="sxs-lookup"><span data-stu-id="68d75-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="68d75-106">Win32 API örneği için aşağıdaki giriş noktası adları içeren **MessageBox** işlevi:</span><span class="sxs-lookup"><span data-stu-id="68d75-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="68d75-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="68d75-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="68d75-108">1-bayt karakter ANSI biçimlendirme, "A" giriş noktası adına göre ayırt sağlar.</span><span class="sxs-lookup"><span data-stu-id="68d75-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="68d75-109">Çağrılar **MessageBoxA** , Windows 95 ve Windows 98 platformlarında yaygın olarak bulunur, ANSI dizelerini sıralama her zaman biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="68d75-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="68d75-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="68d75-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="68d75-111">2-bayt karakter Unicode biçimlendirme, "W" giriş noktası adına göre ayırt sağlar.</span><span class="sxs-lookup"><span data-stu-id="68d75-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="68d75-112">Çağrılar **MessageBoxW** her zaman Windows NT, Windows 2000 ve Windows XP platformlarında yaygın olduğu gibi Unicode biçiminde dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="68d75-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="68d75-113">Dize sıralama ve adı ile eşleşen</span><span class="sxs-lookup"><span data-stu-id="68d75-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="68d75-114">**CharSet** alan aşağıdaki değerleri kabul eder:</span><span class="sxs-lookup"><span data-stu-id="68d75-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="68d75-115">**CharSet.Ansi** (varsayılan değer)</span><span class="sxs-lookup"><span data-stu-id="68d75-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="68d75-116">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="68d75-116">String marshaling</span></span>  
  
     <span data-ttu-id="68d75-117">Platform çağırma sıraladığında dizeleri ANSI biçimine yönetilen biçimlerini (Unicode).</span><span class="sxs-lookup"><span data-stu-id="68d75-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="68d75-118">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="68d75-118">Name matching</span></span>  
  
     <span data-ttu-id="68d75-119">Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır **true**, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="68d75-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="68d75-120">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="68d75-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="68d75-121">Zaman **ExactSpelling** alandır **false**, C++'da varsayılan olarak ve C#, platform çağırma unmangled diğer arar ilk (**MessageBox**), sonra Karıştırılmış adı (**MessageBoxA**) unmangled diğer bulunamaması durumunda.</span><span class="sxs-lookup"><span data-stu-id="68d75-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="68d75-122">ANSI adı eşleştirme davranışı Unicode adıyla eşleşen davranış farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="68d75-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="68d75-123">**DllImport.charset'i**</span><span class="sxs-lookup"><span data-stu-id="68d75-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="68d75-124">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="68d75-124">String marshaling</span></span>  
  
     <span data-ttu-id="68d75-125">Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizeleri Unicode biçiminde.</span><span class="sxs-lookup"><span data-stu-id="68d75-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="68d75-126">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="68d75-126">Name matching</span></span>  
  
     <span data-ttu-id="68d75-127">Zaman **ExactSpelling** alandır **true**, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="68d75-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="68d75-128">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamazsanız başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="68d75-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="68d75-129">Zaman **ExactSpelling** alandır **false**, C++'da varsayılan olarak ve C#, platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), sonra unmangled diğer ad (**MessageBox**) karıştırılmış adı bulunmazsa.</span><span class="sxs-lookup"><span data-stu-id="68d75-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="68d75-130">Unicode adı eşleştirme davranışı ANSI adıyla eşleşen davranış farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="68d75-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="68d75-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="68d75-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="68d75-132">Platform çağırma arasında ANSI ve Unicode biçimlerini hedef platformunu temel alan çalışma zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="68d75-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="68d75-133">Visual Basic'te bir karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="68d75-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="68d75-134">Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her seferinde farklı karakter kümesi davranış.</span><span class="sxs-lookup"><span data-stu-id="68d75-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="68d75-135">Karakter kümesi davranış ekleyerek Visual Basic'te belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="68d75-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="68d75-136">İlk bildirim deyiminde olduğu gibi karakter kümesi anahtar sözcüğü atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ANSI karakter kümesi için varsayılan alan.</span><span class="sxs-lookup"><span data-stu-id="68d75-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="68d75-137">Örnek ikinci ve üçüncü ifadeler karakter kümesi anahtar sözcüğü ile açıkça belirtin.</span><span class="sxs-lookup"><span data-stu-id="68d75-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="68d75-138">İçinde bir karakter kümesi belirtme C# ve C++</span><span class="sxs-lookup"><span data-stu-id="68d75-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="68d75-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68d75-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="68d75-140">Karakter dizesi bağımsız değişkenleri bir yönteme nasıl sıralanması gerektiğini denetimleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="68d75-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="68d75-141">Karakter kümesi belirtmek için aşağıdaki biçimlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="68d75-141">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="68d75-142">Aşağıdaki örnek, üç yönetilen tanımını gösterir **MessageBox** işleve atfedilen karakter kümesi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="68d75-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="68d75-143">İlk tanımında, atlama tarafından **CharSet** ANSI karakter kümesi için varsayılan alan.</span><span class="sxs-lookup"><span data-stu-id="68d75-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68d75-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68d75-144">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="68d75-145">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="68d75-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="68d75-146">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="68d75-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="68d75-147">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="68d75-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
