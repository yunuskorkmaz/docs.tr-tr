---
title: "Giriş Noktası Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7406e256acaea0c535c222386c529c4087bbdc6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="352d3-102">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="352d3-102">Specifying an Entry Point</span></span>
<span data-ttu-id="352d3-103">Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="352d3-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="352d3-104">Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="352d3-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="352d3-105">Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352d3-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="352d3-106">Bir DLL işlevini yeniden adlandırmak için olası nedenlerin bir listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="352d3-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="352d3-107">Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için</span><span class="sxs-lookup"><span data-stu-id="352d3-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="352d3-108">Varolan adlandırma standartlarına uymak için</span><span class="sxs-lookup"><span data-stu-id="352d3-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="352d3-109">Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)</span><span class="sxs-lookup"><span data-stu-id="352d3-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="352d3-110">ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için</span><span class="sxs-lookup"><span data-stu-id="352d3-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="352d3-111">Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="352d3-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="352d3-112">Visual Basic'te bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="352d3-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="352d3-113">Visual Basic kullanan **işlevi** anahtar sözcük **Declare** ayarlamak için ifade <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alan.</span><span class="sxs-lookup"><span data-stu-id="352d3-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="352d3-114">Aşağıdaki örnek, temel bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="352d3-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="352d3-115">Değiştirebileceğiniz **MessageBox** giriş noktasıyla **MsgBox** ekleyerek **diğer** tanımınızı, aşağıdaki örnekte gösterildiği gibi bir anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="352d3-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="352d3-116">Her iki örneklerde **otomatik** anahtar sözcüğü Giriş noktası karakter kümesi sürümünü belirtme ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="352d3-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="352d3-117">Bir karakter seçme hakkında daha fazla bilgi için bkz: [karakter kümesini belirtme](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="352d3-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="352d3-118">C# ve C++'de bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="352d3-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="352d3-119">Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352d3-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="352d3-120">Adı yöntemi tanımınızı işlevi, giriş noktası ile aynı ise DLL'de açıkça işleviyle tanımlamak gerekmez **EntryPoint** alan.</span><span class="sxs-lookup"><span data-stu-id="352d3-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="352d3-121">Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="352d3-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="352d3-122">Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="352d3-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="352d3-123">Aşağıdaki örnekte nasıl değiştirileceğini göstermektedir **MessageBoxA** ile **MsgBox** kullanarak kodunuzda **EntryPoint** alan.</span><span class="sxs-lookup"><span data-stu-id="352d3-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="352d3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="352d3-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="352d3-125">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="352d3-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="352d3-126">Platform çağırma örnekleri</span><span class="sxs-lookup"><span data-stu-id="352d3-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="352d3-127">Platform Çağırma ile veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="352d3-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
