---
title: Giriş noktası belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5449b4fa77ba99a18595077081089e80bd32df
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833615"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="7a4ab-102">Giriş noktası belirtme</span><span class="sxs-lookup"><span data-stu-id="7a4ab-102">Specifying an Entry Point</span></span>

<span data-ttu-id="7a4ab-103">Bir giriş noktası, bir DLL içindeki bir işlevin konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="7a4ab-104">Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıralı giriş noktası, bu işlevi birlikte çalışma sınırları genelinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="7a4ab-105">Ayrıca, giriş noktasını farklı bir adla eşleyebilir ve işlevi etkin bir şekilde yeniden adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="7a4ab-106">Bir DLL işlevini yeniden adlandırmak için olası nedenlerinin bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7a4ab-106">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="7a4ab-107">Büyük/küçük harfe duyarlı API işlev adlarını kullanmaktan kaçınmak için</span><span class="sxs-lookup"><span data-stu-id="7a4ab-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="7a4ab-108">Mevcut adlandırma standartlarıyla uyum sağlamak için</span><span class="sxs-lookup"><span data-stu-id="7a4ab-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="7a4ab-109">Farklı veri türleri alan işlevlere (aynı DLL işlevinin birden çok sürümünü bildirerek) uyum sağlamak için</span><span class="sxs-lookup"><span data-stu-id="7a4ab-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="7a4ab-110">ANSI ve Unicode sürümlerini içeren API 'Leri kullanmayı kolaylaştırmak için</span><span class="sxs-lookup"><span data-stu-id="7a4ab-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="7a4ab-111">Bu konu başlığı altında, Yönetilen koddaki bir DLL işlevinin nasıl yeniden adlandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="7a4ab-112">Visual Basic bir Işlevi yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="7a4ab-112">Renaming a Function in Visual Basic</span></span>  
 
<span data-ttu-id="7a4ab-113">Visual Basic, <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını ayarlamak için **Declare** deyimindeki **Function** anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="7a4ab-114">Aşağıdaki örnek, temel bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-114">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="7a4ab-115">Aşağıdaki örnekte gösterildiği gibi, tanımınıza **diğer ad** anahtar sözcüğünü ekleyerek **MessageBox** giriş noktasını **MsgBox** ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="7a4ab-116">Her iki örnekte de **Auto** anahtar sözcüğü, giriş noktasının karakter kümesi sürümünü belirtme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="7a4ab-117">Bir karakter kümesi seçme hakkında daha fazla bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="7a4ab-117">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="7a4ab-118">Ve içinde C# bir işlevi yeniden adlandırmaC++</span><span class="sxs-lookup"><span data-stu-id="7a4ab-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="7a4ab-119">Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="7a4ab-120">Yöntem tanımınızdaki işlevin adı DLL 'deki giriş noktasıyla aynıysa, işlevi **entryPoint** alanı ile açıkça belirlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="7a4ab-121">Aksi takdirde, bir ad veya sıra belirtmek için aşağıdaki öznitelik formlarından birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="7a4ab-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="7a4ab-122">Numara işareti (#) ile bir sıra öneki yapmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="7a4ab-123">Aşağıdaki örnek, **giriş noktası** alanını kullanarak kodunuzda bir **MsgBox** ile **MessageBoxA** 'nın nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
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
  
## <a name="see-also"></a><span data-ttu-id="7a4ab-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a4ab-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="7a4ab-125">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a4ab-125">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="7a4ab-126">Platform çağırma örnekleri</span><span class="sxs-lookup"><span data-stu-id="7a4ab-126">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="7a4ab-127">Platform çağırma ile verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="7a4ab-127">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
