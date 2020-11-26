---
title: MsgBox Örneği
description: String türlerini, MsgBox kullanarak parametrelere göre değerlere göre geçirme örneğine bakın. .NET 'teki EntryPoint, CharSet ve ExactSpelling alanlarının ne zaman kullanılacağını gösterir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: 024ed612115ce73646596651fe454238418446db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242025"
---
# <a name="msgbox-sample"></a><span data-ttu-id="5ac23-104">MsgBox Örneği</span><span class="sxs-lookup"><span data-stu-id="5ac23-104">MsgBox Sample</span></span>

<span data-ttu-id="5ac23-105">Bu örnek, parametre türlerini parametrelere göre ve,, ve alanlarını ne zaman kullanacağınızı gösteren bir değere göre nasıl geçirileceğini gösterir <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint> <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> .</span><span class="sxs-lookup"><span data-stu-id="5ac23-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="5ac23-106">MsgBox örnek, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="5ac23-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="5ac23-107">User32.dll 'den dışarıya aktarılmış **MessageBox** .</span><span class="sxs-lookup"><span data-stu-id="5ac23-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="5ac23-108">Bu örnekte, sınıfı, `NativeMethods` sınıfı tarafından çağrılan her yönetilmeyen işlev için bir yönetilen prototip içerir `MsgBoxSample` .</span><span class="sxs-lookup"><span data-stu-id="5ac23-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="5ac23-109">Yönetilen prototip yöntemleri, `MsgBox` `MsgBox2` ve `MsgBox3` aynı yönetilmeyen işlev için farklı bildirimlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5ac23-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="5ac23-110">`MsgBox2`ANSI olarak belirtilen karakter türü, Unicode işlevinin adı olan giriş noktasıyla eşleşmediğinden, için bildirimi ileti kutusunda yanlış çıktı üretir `MessageBoxW` .</span><span class="sxs-lookup"><span data-stu-id="5ac23-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="5ac23-111">Bildirimi, `MsgBox3` **entryPoint**, **charset** ve **ExactSpelling** alanları arasında bir uyumsuzluk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ac23-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="5ac23-112">Çağrıldığında `MsgBox3` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ac23-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="5ac23-113">Dize adlandırma ve ad sıralaması hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="5ac23-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="5ac23-114">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="5ac23-114">Declaring Prototypes</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="5ac23-115">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="5ac23-115">Calling Functions</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac23-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac23-116">See also</span></span>

- [<span data-ttu-id="5ac23-117">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5ac23-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="5ac23-118">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5ac23-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="5ac23-119">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ac23-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="5ac23-120">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="5ac23-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
