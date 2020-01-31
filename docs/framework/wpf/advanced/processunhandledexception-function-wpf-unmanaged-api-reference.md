---
title: ProcessUnhandledException Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743926"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException Işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Özel durum işleme için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>Parametreler  
 errorMsg  
 Hata iletisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **DOSYASıNı**  
  
 .NET Framework 3,0 ve 3,5: PresentationHostDLL. dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400. dll  
  
 **.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
