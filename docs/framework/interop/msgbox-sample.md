---
title: MsgBox Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: b970a5a193f82ca141c030491febce5ef352eb70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181353"
---
# <a name="msgbox-sample"></a><span data-ttu-id="797db-102">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="797db-102">MsgBox Sample</span></span>
<span data-ttu-id="797db-103">Bu örnek <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, parametre türlerini parametrelere göre ve, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanlarını ne zaman kullanacağınızı gösteren bir değere göre nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="797db-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="797db-104">MsgBox örnek, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="797db-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="797db-105">User32. dll dosyasından aktarılmış **MessageBox** .</span><span class="sxs-lookup"><span data-stu-id="797db-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="797db-106">Bu örnekte, `NativeMethods` sınıfı, `MsgBoxSample` sınıfı tarafından çağrılan her yönetilmeyen işlev için bir yönetilen prototip içerir.</span><span class="sxs-lookup"><span data-stu-id="797db-106">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="797db-107">Yönetilen prototip yöntemleri `MsgBox` `MsgBox2`, ve `MsgBox3` aynı yönetilmeyen işlev için farklı bildirimlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="797db-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="797db-108">ANSI olarak belirtilen `MsgBox2` karakter türü, Unicode işlevinin adı olan giriş noktasıyla `MessageBoxW`eşleşmediğinden, için bildirimi ileti kutusunda yanlış çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="797db-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="797db-109">`MsgBox3` Bildirimi, **entryPoint**, **charset**ve **ExactSpelling** alanları arasında bir uyumsuzluk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="797db-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="797db-110">Çağrıldığında bir özel `MsgBox3` durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="797db-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="797db-111">Dize adlandırma ve ad sıralaması hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="797db-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="797db-112">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="797db-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="797db-113">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="797db-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="797db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="797db-114">See also</span></span>

- [<span data-ttu-id="797db-115">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="797db-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="797db-116">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="797db-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="797db-117">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="797db-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="797db-118">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="797db-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
