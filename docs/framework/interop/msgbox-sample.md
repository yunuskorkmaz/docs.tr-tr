---
title: MsgBox Örneği
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26c72ee918db48bcbdf0ce912e12d20a0719f85b
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="msgbox-sample"></a><span data-ttu-id="11829-102">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="11829-102">MsgBox Sample</span></span>
<span data-ttu-id="11829-103">Bu örnek parametreleri olduğu gibi değeriyle dize türleri geçirmek nasıl ve ne zaman kullanılacağı gösterilmektedir <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanları.</span><span class="sxs-lookup"><span data-stu-id="11829-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="11829-104">MsgBox örneği özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="11829-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="11829-105">**MessageBox** User32.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="11829-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="11829-106">Bu örnekte `LibWrap` sınıfı tarafından çağrılır her yönetilmeyen işlevi için yönetilen bir prototip içerir `MsgBoxSample` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11829-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="11829-107">Yönetilen prototip yöntemleri `MsgBox`, `MsgBox2`, ve `MsgBox3` aynı için farklı bildirimleri işlevi yönetilmeyen sahip.</span><span class="sxs-lookup"><span data-stu-id="11829-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="11829-108">Bildirimi `MsgBox2` , ANSI karakter belirtildi giriş noktası ile uyumsuz olduğundan ileti kutusunda yanlış bir çıktı üretir `MessageBoxW`, Unicode işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="11829-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="11829-109">Bildirimi `MsgBox3` arasında bir uyuşmazlık oluşturur **EntryPoint**, **CharSet**, ve **ExactSpelling** alanları.</span><span class="sxs-lookup"><span data-stu-id="11829-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="11829-110">Çağrıldığında, `MsgBox3` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11829-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="11829-111">Dize adlandırma ve ad hazırlama hakkında ayrıntılı bilgi için bkz: [karakter kümesini belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="11829-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="11829-112">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="11829-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="11829-113">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="11829-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="11829-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11829-114">See Also</span></span>  
 [<span data-ttu-id="11829-115">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="11829-115">Marshaling Strings</span></span>](marshaling-strings.md)  
 <span data-ttu-id="11829-116">[Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11829-116">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="11829-117">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="11829-117">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)  
 [<span data-ttu-id="11829-118">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="11829-118">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="11829-119">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="11829-119">Specifying a Character Set</span></span>](specifying-a-character-set.md)
