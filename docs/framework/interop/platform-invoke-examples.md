---
title: Platform Çağırma Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37a864083fa7cfbea16614a94454571f31deed3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872618"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="db044-102">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="db044-102">Platform Invoke Examples</span></span>
<span data-ttu-id="db044-103">Aşağıdaki örnekler çağırmak nasıl gösterir **MessageBox** User32.dll, basit bir dize bağımsız değişken geçirme işlevi.</span><span class="sxs-lookup"><span data-stu-id="db044-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="db044-104">Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ayarlanmış **otomatik** karakter genişliği belirlemek ve dize sıralama hedef platform izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="db044-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="db044-105">Diğer örnekler için [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="db044-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db044-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db044-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="db044-107">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db044-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="db044-108">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="db044-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
