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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3393adf5beed02a5a4bda2e07bd26e29e47fae2f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219314"
---
# <a name="msgbox-sample"></a><span data-ttu-id="abd51-102">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="abd51-102">MsgBox Sample</span></span>
<span data-ttu-id="abd51-103">Bu örnek, dize türleri parametre değeri olarak geçirmek nasıl ve ne zaman kullanılacağını gösterir. <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanları.</span><span class="sxs-lookup"><span data-stu-id="abd51-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="abd51-104">MsgBox örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="abd51-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="abd51-105">**MessageBox** User32.dll dışarı aktarılan.</span><span class="sxs-lookup"><span data-stu-id="abd51-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="abd51-106">Bu örnekte `LibWrap` sınıfı içeren yönetilen prototip çağrılan yönetilmeyen her işlev için `MsgBoxSample` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="abd51-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="abd51-107">Yönetilen prototip yöntemlerini `MsgBox`, `MsgBox2`, ve `MsgBox3` farklı bildirimleri için aynı işlev yönetilmeyen sahip.</span><span class="sxs-lookup"><span data-stu-id="abd51-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="abd51-108">Bildirimi `MsgBox2` ANSI belirtilen karakter türü, giriş noktası ile uyumsuz olduğundan ileti kutusunda yanlış bir çıktı üretir `MessageBoxW`, Unicode işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="abd51-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="abd51-109">Bildirimi `MsgBox3` arasında bir uyuşmazlık oluşturur **EntryPoint**, **CharSet**, ve **ExactSpelling** alanları.</span><span class="sxs-lookup"><span data-stu-id="abd51-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="abd51-110">Çağrıldığında, `MsgBox3` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abd51-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="abd51-111">Dize adlandırma ve ad hazırlama hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="abd51-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="abd51-112">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="abd51-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="abd51-113">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="abd51-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="abd51-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abd51-114">See also</span></span>
- [<span data-ttu-id="abd51-115">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="abd51-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="abd51-116">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="abd51-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="abd51-117">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="abd51-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="abd51-118">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="abd51-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
