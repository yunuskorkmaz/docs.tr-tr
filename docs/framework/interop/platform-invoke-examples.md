---
title: "Platform Çağırma Örnekleri"
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
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 892d014060de869959835dc980a8d153908ca63c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="c0c28-102">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c0c28-102">Platform Invoke Examples</span></span>
<span data-ttu-id="c0c28-103">Aşağıdaki örnekler tanımlayın ve çağırmak nasıl göstermektedir **MessageBox** basit bir dize bağımsız değişken olarak geçirme User32.dll işlevinde.</span><span class="sxs-lookup"><span data-stu-id="c0c28-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="c0c28-104">Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan ayarlanmış **otomatik** karakter genişliğini belirlemek ve dize sıralama hedef platformu izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="c0c28-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="c0c28-105">Ek örnekler için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c0c28-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c28-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0c28-106">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="c0c28-107">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0c28-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="c0c28-108">Karakter kümesi belirtme</span><span class="sxs-lookup"><span data-stu-id="c0c28-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
