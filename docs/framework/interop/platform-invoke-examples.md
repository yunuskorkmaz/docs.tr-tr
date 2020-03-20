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
ms.openlocfilehash: 358d1ce662d56b8c31124f4b3264ec25a0f94586
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181327"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="9cfc0-102">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9cfc0-102">Platform Invoke Examples</span></span>
<span data-ttu-id="9cfc0-103">Aşağıdaki örnekler, User32.dll'de **MessageBox** işlevinin nasıl tanımlanacağını ve çağıracağını ve basit bir dizeyi bağımsız değişken olarak nasıl geçeceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cfc0-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="9cfc0-104">Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan, hedef platformun karakter genişliğini ve dize mareşalliğini belirlemesini sağlamak için **Otomatik** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9cfc0-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="9cfc0-105">Ek örnekler için [bkz.](marshaling-data-with-platform-invoke.md)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfc0-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cfc0-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="9cfc0-107">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cfc0-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="9cfc0-108">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="9cfc0-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
