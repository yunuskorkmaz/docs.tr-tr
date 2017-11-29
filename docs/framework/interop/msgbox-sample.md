---
title: "MsgBox Örneği"
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
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d9be3d490a687541a0b1c7af3d90c52523413a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="msgbox-sample"></a><span data-ttu-id="fd643-102">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="fd643-102">MsgBox Sample</span></span>
<span data-ttu-id="fd643-103">Bu örnek parametreleri olduğu gibi değeriyle dize türleri geçirmek nasıl ve ne zaman kullanılacağı gösterilmektedir <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanları.</span><span class="sxs-lookup"><span data-stu-id="fd643-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="fd643-104">MsgBox örneği özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="fd643-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="fd643-105">**MessageBox** User32.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="fd643-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="fd643-106">Bu örnekte `LibWrap` sınıfı tarafından çağrılır her yönetilmeyen işlevi için yönetilen bir prototip içerir `MsgBoxSample` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fd643-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="fd643-107">Yönetilen prototip yöntemleri `MsgBox`, `MsgBox2`, ve `MsgBox3` aynı için farklı bildirimleri işlevi yönetilmeyen sahip.</span><span class="sxs-lookup"><span data-stu-id="fd643-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="fd643-108">Bildirimi `MsgBox2` , ANSI karakter belirtildi giriş noktası ile uyumsuz olduğundan ileti kutusunda yanlış bir çıktı üretir `MessageBoxW`, Unicode işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="fd643-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="fd643-109">Bildirimi `MsgBox3` arasında bir uyuşmazlık oluşturur **EntryPoint**, **CharSet**, ve **ExactSpelling** alanları.</span><span class="sxs-lookup"><span data-stu-id="fd643-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="fd643-110">Çağrıldığında, `MsgBox3` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd643-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="fd643-111">Dize adlandırma ve ad hazırlama hakkında ayrıntılı bilgi için bkz: [karakter kümesini belirtme](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="fd643-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="fd643-112">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="fd643-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="fd643-113">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="fd643-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fd643-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd643-114">See Also</span></span>  
 [<span data-ttu-id="fd643-115">Dizeleri hazırlama</span><span class="sxs-lookup"><span data-stu-id="fd643-115">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="fd643-116">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="fd643-116">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="fd643-117">Dizeler için varsayılan hazırlama</span><span class="sxs-lookup"><span data-stu-id="fd643-117">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [<span data-ttu-id="fd643-118">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd643-118">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="fd643-119">Karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="fd643-119">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
