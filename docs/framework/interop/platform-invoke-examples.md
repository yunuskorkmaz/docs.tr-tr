---
title: Platform Çağırma Örnekleri
description: User32.dll ' de MessageBox işlevinin nasıl tanımlanacağını ve çağrılacağını gösteren platform çağırma örneğine bakın.
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
ms.openlocfilehash: 3b626061a579e089f92f2bf7de7f83f7db5bd184
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268891"
---
# <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri

Aşağıdaki örnekler, bir bağımsız değişken olarak basit bir dize geçirerek User32.dll **MessageBox** işlevinin nasıl tanımlanacağını ve çağrılacağını gösterir. Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan, hedef platformun karakter genişliğini ve dize sıralamasını belirlemesine izin vermek Için **Auto** olarak ayarlanır.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Ek örnekler için bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [Karakter Kümesi Belirtme](specifying-a-character-set.md)
