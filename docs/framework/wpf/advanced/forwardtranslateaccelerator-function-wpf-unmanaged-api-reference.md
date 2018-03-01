---
title: "ForwardTranslateAccelerator işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cca9c78eaf13e04d22fce9f61ce4a7ab9ee09769
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a>Parametreler  
 pMsg  
 Bir ileti için bir işaretçi.  
  
 appUnhandled  
 `true`ne zaman uygulama zaten giriş iletiyi işlemek için bir fırsat verildi, ancak bunu işlediği değil; Aksi takdirde `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400.dll  
  
 **.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Yönetilmeyen API Başvurusu](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
