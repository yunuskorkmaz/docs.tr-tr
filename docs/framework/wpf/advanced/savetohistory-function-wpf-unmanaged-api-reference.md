---
title: SaveToHistory işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 680c63548482c413a7ceff24a4f38eed589f4682
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745278"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a>Parametreler  
 pHistoryStream  
 Geçmiş akış için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400.dll  
  
 **.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Yönetilmeyen API Başvurusu](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
