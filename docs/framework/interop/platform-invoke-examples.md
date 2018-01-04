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
ms.workload: dotnet
ms.openlocfilehash: 1a4533aa1cef5d400fff0c8d3169b0b1edc22eab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri
Aşağıdaki örnekler tanımlayın ve çağırmak nasıl göstermektedir **MessageBox** basit bir dize bağımsız değişken olarak geçirme User32.dll işlevinde. Örneklerde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> alan ayarlanmış **otomatik** karakter genişliğini belirlemek ve dize sıralama hedef platformu izin vermek için.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Ek örnekler için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Karakter Kümesi Belirtme](../../../docs/framework/interop/specifying-a-character-set.md)
