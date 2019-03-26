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
ms.openlocfilehash: 0146d3617f5a4aff2a76d2b2f4777b18a0e9c2ab
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410825"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="30cdc-102">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="30cdc-102">Specifying a Character Set</span></span>
<span data-ttu-id="30cdc-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan denetimleri dize sıralama ve platform çağırma DLL'de bulur işlev adlarını nasıl belirler.</span><span class="sxs-lookup"><span data-stu-id="30cdc-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="30cdc-104">Bu konuda, hem davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30cdc-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="30cdc-105">Bazı API'leri iki dize bağımsız değişkenler almayan işlevleri sürümü dışarı aktar: (ANSI) dar ve geniş (Unicode).</span><span class="sxs-lookup"><span data-stu-id="30cdc-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="30cdc-106">Windows API, örneğin, aşağıdaki giriş noktası adları içerir **MessageBox** işlevi:</span><span class="sxs-lookup"><span data-stu-id="30cdc-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="30cdc-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="30cdc-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="30cdc-108">1-bayt karakter ANSI biçimlendirme, "A" giriş noktası adına göre ayırt sağlar.</span><span class="sxs-lookup"><span data-stu-id="30cdc-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="30cdc-109">Çağrılar **MessageBoxA** , Windows 95 ve Windows 98 platformlarında yaygın olarak bulunur, ANSI dizelerini sıralama her zaman biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="30cdc-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="30cdc-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="30cdc-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="30cdc-111">2-bayt karakter Unicode biçimlendirme, "W" giriş noktası adına göre ayırt sağlar.</span><span class="sxs-lookup"><span data-stu-id="30cdc-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="30cdc-112">Çağrılar **MessageBoxW** her zaman Windows NT, Windows 2000 ve Windows XP platformlarında yaygın olduğu gibi Unicode biçiminde dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="30cdc-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="30cdc-113">Dize sıralama ve adı ile eşleşen</span><span class="sxs-lookup"><span data-stu-id="30cdc-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="30cdc-114">`CharSet` Alan aşağıdaki değerleri kabul eder:</span><span class="sxs-lookup"><span data-stu-id="30cdc-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="30cdc-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (varsayılan değer)</span><span class="sxs-lookup"><span data-stu-id="30cdc-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
-   <span data-ttu-id="30cdc-116">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="30cdc-116">String marshaling</span></span>  
  
     <span data-ttu-id="30cdc-117">Platform çağırma sıraladığında dizeleri ANSI biçimine yönetilen biçimlerini (Unicode).</span><span class="sxs-lookup"><span data-stu-id="30cdc-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="30cdc-118">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="30cdc-118">Name matching</span></span>  
  
     <span data-ttu-id="30cdc-119">Zaman <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> alandır `true`, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="30cdc-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="30cdc-120">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamadığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="30cdc-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="30cdc-121">Zaman `ExactSpelling` alandır `false`, C++'da varsayılan olarak ve C#, platform çağırma unmangled diğer arar ilk (**MessageBox**), ardından karıştırılmış adı (**MessageBoxA**) unmangled diğer bulunamaması durumunda.</span><span class="sxs-lookup"><span data-stu-id="30cdc-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="30cdc-122">ANSI adı eşleştirme davranışı Unicode adıyla eşleşen davranış farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="30cdc-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   <span data-ttu-id="30cdc-123">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="30cdc-123">String marshaling</span></span>  
  
     <span data-ttu-id="30cdc-124">Platform çağırma yönetilen biçimlerini (Unicode) kopyaları dizeleri Unicode biçiminde.</span><span class="sxs-lookup"><span data-stu-id="30cdc-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="30cdc-125">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="30cdc-125">Name matching</span></span>  
  
     <span data-ttu-id="30cdc-126">Zaman `ExactSpelling` alandır `true`, varsayılan olarak olduğu gibi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform çağırma yalnızca belirttiğiniz ad arar.</span><span class="sxs-lookup"><span data-stu-id="30cdc-126">When the `ExactSpelling` field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="30cdc-127">Örneğin, belirtirseniz **MessageBox**, platform çağırma arar **MessageBox** ve tam yazım bulamazsanız başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="30cdc-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="30cdc-128">Zaman `ExactSpelling` alandır `false`, C++'da varsayılan olarak ve C#, platform çağırma karıştırılmış ad arar ilk (**MessageBoxW**), ardından unmangled diğer ad (**MessageBox**) karıştırılmış adı bulunmazsa.</span><span class="sxs-lookup"><span data-stu-id="30cdc-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="30cdc-129">Unicode adı eşleştirme davranışı ANSI adıyla eşleşen davranış farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="30cdc-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   <span data-ttu-id="30cdc-130">Platform çağırma arasında ANSI ve Unicode biçimlerini hedef platformunu temel alan çalışma zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="30cdc-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="30cdc-131">Visual Basic'te bir karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="30cdc-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="30cdc-132">Aşağıdaki örnek bildirir **MessageBox** işlevi üç kez, her seferinde farklı karakter kümesi davranış.</span><span class="sxs-lookup"><span data-stu-id="30cdc-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="30cdc-133">Karakter kümesi davranış ekleyerek Visual Basic'te belirtebilirsiniz **ANSI**, **Unicode**, veya **otomatik** bildirim deyiminin anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="30cdc-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="30cdc-134">İlk bildirim deyiminde olduğu gibi karakter kümesi anahtar sözcüğü atlarsanız <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ANSI karakter kümesi için varsayılan alan.</span><span class="sxs-lookup"><span data-stu-id="30cdc-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="30cdc-135">Örnek ikinci ve üçüncü ifadeler karakter kümesi anahtar sözcüğü ile açıkça belirtin.</span><span class="sxs-lookup"><span data-stu-id="30cdc-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="30cdc-136">İçinde bir karakter kümesi belirtme C# ve C++</span><span class="sxs-lookup"><span data-stu-id="30cdc-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="30cdc-137"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Alan temel karakter ANSI veya Unicode olarak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30cdc-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="30cdc-138">Karakter dizesi bağımsız değişkenleri bir yönteme nasıl sıralanması gerektiğini denetimleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="30cdc-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="30cdc-139">Karakter kümesi belirtmek için aşağıdaki biçimlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="30cdc-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="30cdc-140">Aşağıdaki örnek, üç yönetilen tanımını gösterir **MessageBox** işleve atfedilen karakter kümesi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="30cdc-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="30cdc-141">İlk tanımında, atlama tarafından `CharSet` ANSI karakter kümesi için varsayılan alan.</span><span class="sxs-lookup"><span data-stu-id="30cdc-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30cdc-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30cdc-142">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="30cdc-143">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="30cdc-143">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="30cdc-144">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="30cdc-144">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="30cdc-145">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="30cdc-145">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
