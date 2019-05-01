---
title: Giriş Noktası Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15a441ea7b0b16c83c590289d04cf0c10623fb85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032763"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="a6ef5-102">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="a6ef5-102">Specifying an Entry Point</span></span>
<span data-ttu-id="a6ef5-103">Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="a6ef5-104">Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="a6ef5-105">Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="a6ef5-106">Bir DLL işlevini yeniden adlandırmak için olası nedenlerin bir listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="a6ef5-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="a6ef5-107">Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için</span><span class="sxs-lookup"><span data-stu-id="a6ef5-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="a6ef5-108">Varolan adlandırma standartlarına uymak için</span><span class="sxs-lookup"><span data-stu-id="a6ef5-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="a6ef5-109">Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)</span><span class="sxs-lookup"><span data-stu-id="a6ef5-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="a6ef5-110">ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için</span><span class="sxs-lookup"><span data-stu-id="a6ef5-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="a6ef5-111">Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="a6ef5-112">Visual Basic'te bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a6ef5-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="a6ef5-113">Visual Basic kullanan **işlevi** anahtar sözcüğünü **Declare** ayarlamak için ifade <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alan.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="a6ef5-114">Aşağıdaki örnek, temel bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-114">The following example shows a basic declaration.</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="a6ef5-115">Değiştirebilirsiniz **MessageBox** giriş noktasıyla **MsgBox** ekleyerek **diğer** aşağıdaki örnekte gösterildiği gibi tanımınızı, anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="a6ef5-116">Her iki örnek **otomatik** anahtar sözcüğü giriş noktasının karakter kümesi sürümünü belirtme ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="a6ef5-117">Bir karakter seçme hakkında daha fazla bilgi için bkz: [bir karakter kümesi belirtme](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="a6ef5-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="a6ef5-118">C# ve C++'de bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a6ef5-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="a6ef5-119">Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="a6ef5-120">Yöntem tanımınızdaki işlevin adı giriş noktasıyla aynıysa DLL'deki işlevi açıkça tanımlamak gerekmez **EntryPoint** alan.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="a6ef5-121">Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a6ef5-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="a6ef5-122">Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="a6ef5-123">Aşağıdaki örnek nasıl değiştirileceğini gösterir **MessageBoxA** ile **MsgBox** kullanarak kodunuzda **EntryPoint** alan.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
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
  
## <a name="see-also"></a><span data-ttu-id="a6ef5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6ef5-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="a6ef5-125">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6ef5-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="a6ef5-126">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a6ef5-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="a6ef5-127">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a6ef5-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
