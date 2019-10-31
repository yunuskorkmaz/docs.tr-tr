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
ms.openlocfilehash: 9f1e6d58742f60b6043a4be9218b80b323cd523e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124107"
---
# <a name="msgbox-sample"></a><span data-ttu-id="36439-102">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="36439-102">MsgBox Sample</span></span>
<span data-ttu-id="36439-103">Bu örnek, dize türlerini parametrelere göre ve <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanlarının ne zaman kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36439-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="36439-104">MsgBox örnek, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="36439-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="36439-105">User32. dll dosyasından aktarılmış **MessageBox** .</span><span class="sxs-lookup"><span data-stu-id="36439-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="36439-106">Bu örnekte, `NativeMethods` sınıfı, `MsgBoxSample` sınıfı tarafından çağrılan her yönetilmeyen işlev için bir yönetilen prototip içerir.</span><span class="sxs-lookup"><span data-stu-id="36439-106">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="36439-107">`MsgBox`, `MsgBox2`ve `MsgBox3` yönetilen prototip yöntemleri aynı yönetilmeyen işlev için farklı bildirimlere sahip.</span><span class="sxs-lookup"><span data-stu-id="36439-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="36439-108">`MsgBox2` bildirimi, ileti kutusunda hatalı çıkış üretir çünkü ANSI olarak belirtilen karakter türü, Unicode işlevinin adı olan `MessageBoxW`giriş noktası ile eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="36439-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="36439-109">`MsgBox3` bildirimi, **entryPoint**, **charset**ve **ExactSpelling** alanları arasında bir uyumsuzluk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36439-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="36439-110">Çağrıldığında, `MsgBox3` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36439-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="36439-111">Dize adlandırma ve ad sıralaması hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="36439-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="36439-112">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="36439-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="36439-113">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="36439-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="36439-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36439-114">See also</span></span>

- [<span data-ttu-id="36439-115">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="36439-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="36439-116">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="36439-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="36439-117">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36439-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="36439-118">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="36439-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
