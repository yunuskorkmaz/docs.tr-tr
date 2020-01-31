---
title: ForwardTranslateAccelerator Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747041"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator Işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Parametreler  
 pMsg  
 İleti işaretçisi.  
  
 Appişlenmemiş  
 uygulamaya giriş iletisini işleme şansı verildiğinde, ancak işlenmeyen `true`; Aksi takdirde, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **DOSYASıNı**  
  
 .NET Framework 3,0 ve 3,5: PresentationHostDLL. dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400. dll  
  
 **.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
