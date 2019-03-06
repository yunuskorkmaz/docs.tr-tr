---
title: ForwardTranslateAccelerator işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 02d5d23ec44d9fb7a244fc635ac174cf81ead173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362194"
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
 `true` ne zaman uygulama giriş iletisini işlemek için bir fırsat verildi, ancak bunun işlediği değil; Aksi takdirde, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400.dll  
  
 **.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
