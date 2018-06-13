---
title: LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 19674b45af84e1e6a6ca169f7b6654c6e3847416
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544670"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>Parametreler  
 pHistoryStream  
 Bir işaretçi bir akışa geçmiş bilgileri.  
  
 pBindCtx  
 Bir bağlama bağlamı için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400.dll  
  
 **.NET framework sürüm:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Yönetilmeyen API Başvurusu](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
