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
ms.openlocfilehash: da157a40819ada3914cf1791c8ca3f7b30e8c837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124754"
---
# <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri
Aşağıdaki örnekler, bir bağımsız değişken olarak basit bir dize geçirerek User32. dll ' de **MessageBox** işlevinin nasıl tanımlanacağını ve çağrılacağını gösterir. Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alanı **Auto** olarak ayarlanır ve hedef platformun karakter genişliğini ve dize sıralamasını belirlemesine izin verir.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Ek örnekler için bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [Karakter Kümesi Belirtme](specifying-a-character-set.md)
