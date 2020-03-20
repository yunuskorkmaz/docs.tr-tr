---
title: LoadFromHistory Fonksiyonu - WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141581"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory Fonksiyonu (WPF Yönetilmeyen API Başvurusu)
Bu API, Windows Sunu Temeli (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.  
  
 Windows Yönetimi için Windows Sunu Temeli (WPF) altyapısı tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Parametreler  
 pHistoryAAkışı  
 Geçmiş bilgi akışıiçin bir işaretçi.  
  
 pBindCtx  
 Bağlama bağlamına işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [.NET Çerçeve Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve sonraki olarak: PresentationHost_v0400.dll  
  
 **.NET Çerçeve Sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
