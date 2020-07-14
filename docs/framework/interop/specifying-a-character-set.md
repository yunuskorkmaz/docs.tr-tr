---
title: Karakter Kümesi Belirtme
description: Dar (ANSI) veya geniş (Unicode) kodlama kullanan bir karakter kümesi belirtmeyi öğrenin. Alternatif olarak otomatik çalışma zamanı seçimini belirtebilirsiniz.
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
ms.openlocfilehash: a4f18431d89343a77ccf2b920edac485e7dcfca3
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282131"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="96c13-104">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="96c13-104">Specifying a Character Set</span></span>
<span data-ttu-id="96c13-105"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Alan, dize sıralamasını denetler ve platform çağırma işlevinin BIR DLL 'de işlev adlarını bulmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="96c13-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="96c13-106">Bu konuda her iki davranış de açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96c13-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="96c13-107">Bazı API 'Ler dize bağımsız değişkenleri alan işlevlerin iki sürümünü dışarı aktarır: dar (ANSI) ve geniş (Unicode).</span><span class="sxs-lookup"><span data-stu-id="96c13-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="96c13-108">Örneğin, Windows API 'SI, **MessageBox** işlevi için aşağıdaki giriş noktası adlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="96c13-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="96c13-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="96c13-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="96c13-110">Giriş noktası adına bir "A" eklenerek ayırt edilen 1 baytlık karakter ANSI biçimlendirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c13-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="96c13-111">Her zaman ANSI biçimindeki **MessageBoxA** çağrısı dizeleri.</span><span class="sxs-lookup"><span data-stu-id="96c13-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="96c13-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="96c13-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="96c13-113">Giriş noktası adına bir "W" ile ayırt edilen 2 baytlık karakter Unicode biçimlendirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c13-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="96c13-114">**MessageBoxW** çağrıları her zaman Unicode biçiminde dizeleri sıralama.</span><span class="sxs-lookup"><span data-stu-id="96c13-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="96c13-115">Dize hazırlama ve ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="96c13-115">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="96c13-116">`CharSet`Alan, aşağıdaki değerleri kabul eder:</span><span class="sxs-lookup"><span data-stu-id="96c13-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="96c13-117"><xref:System.Runtime.InteropServices.CharSet.Ansi>(varsayılan değer)</span><span class="sxs-lookup"><span data-stu-id="96c13-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="96c13-118">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="96c13-118">String marshaling</span></span>  
  
     <span data-ttu-id="96c13-119">Platform, yönetilen biçimindeki (Unicode) dizeleri ANSI biçimine göre sıralamalarını çağırır.</span><span class="sxs-lookup"><span data-stu-id="96c13-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="96c13-120">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="96c13-120">Name matching</span></span>  
  
     <span data-ttu-id="96c13-121">Alan, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> Visual Basic varsayılan olarak olduğunda, `true` Platform Invoke yalnızca belirttiğiniz ad için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="96c13-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="96c13-122">Örneğin, **MessageBox**belirtirseniz, platform çağrısı, **MessageBox** için arama yapar ve tam yazımı bulamıyorsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="96c13-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="96c13-123">Alan, `ExactSpelling` `false` C++ ve C# ' de varsayılan olarak olduğu gibi, platform Invoke First unkarışmış diğer ad (**MessageBox**), daha sonra da unkarıştırılmış diğer ad bulunamazsa karıştırılmış adı (**MessageBoxA**) arar.</span><span class="sxs-lookup"><span data-stu-id="96c13-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="96c13-124">ANSI ad eşleştirme davranışının Unicode ad eşleştirme davranışından farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="96c13-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="96c13-125">Dize sıralama</span><span class="sxs-lookup"><span data-stu-id="96c13-125">String marshaling</span></span>  
  
     <span data-ttu-id="96c13-126">Platform çağrısı, dizeleri yönetilen biçiminden (Unicode) Unicode biçimine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="96c13-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="96c13-127">Ad eşleştirme</span><span class="sxs-lookup"><span data-stu-id="96c13-127">Name matching</span></span>  
  
     <span data-ttu-id="96c13-128">Alan, `ExactSpelling` Visual Basic varsayılan olarak olduğunda, `true` Platform Invoke yalnızca belirttiğiniz ad için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="96c13-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="96c13-129">Örneğin, **MessageBox**belirtirseniz, Platform **çağırın ve tam** yazım bulamazsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="96c13-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="96c13-130">Alan, `ExactSpelling` `false` C++ ve C# ' de varsayılan olarak olduğu gibi, platform Invoke önce karışmış adı arar (**MessageBoxW**), ardından karışmış ad bulunamazsa, Unkarıştırılmış diğer ad (**MessageBox**).</span><span class="sxs-lookup"><span data-stu-id="96c13-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="96c13-131">Unicode ad eşleştirme davranışının ANSI ad eşleştirme davranışından farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="96c13-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="96c13-132">Platform çağırma, hedef platforma bağlı olarak çalışma zamanında ANSI ve Unicode biçimleri arasında seçer.</span><span class="sxs-lookup"><span data-stu-id="96c13-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="96c13-133">Visual Basic bir karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="96c13-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="96c13-134">Aşağıdaki örnek, her seferinde farklı karakter kümesi davranışına sahip olan **MessageBox** işlevini üç kez bildirir.</span><span class="sxs-lookup"><span data-stu-id="96c13-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="96c13-135">Bildirim bildirimine **Ansi**, **UNICODE**veya **Auto** anahtar sözcüğünü ekleyerek Visual Basic karakter kümesi davranışını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96c13-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="96c13-136">Karakter kümesi anahtar sözcüğünü atlarsanız, ilk bildirim ifadesinde yapıldığı gibi, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan varsayılan olarak ANSI karakter kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="96c13-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="96c13-137">Örnekteki ikinci ve üçüncü deyimler, anahtar sözcüğü olan bir karakter kümesini açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="96c13-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="96c13-138">C# ve C++ içinde bir karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="96c13-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="96c13-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Alan, temel alınan karakter KÜMESINI ANSI veya Unicode olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="96c13-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="96c13-140">Karakter kümesi bir yönteme dize bağımsız değişkenlerinin nasıl sıralanması gerektiğini denetler.</span><span class="sxs-lookup"><span data-stu-id="96c13-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="96c13-141">Karakter kümesini belirtmek için aşağıdaki formlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="96c13-141">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="96c13-142">Aşağıdaki örnek, bir karakter kümesi belirtmeye yönelik **MessageBox** işlevinin üç Yönetilen tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96c13-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="96c13-143">İlk tanımda, atlanarak, `CharSet` alan varsayılan olarak ANSI karakter kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="96c13-143">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96c13-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96c13-144">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="96c13-145">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96c13-145">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="96c13-146">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="96c13-146">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="96c13-147">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="96c13-147">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
