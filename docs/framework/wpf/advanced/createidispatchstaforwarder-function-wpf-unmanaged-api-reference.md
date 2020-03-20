---
title: CreateIDispatchSTAForwarder Fonksiyonu - WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174725"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder Fonksiyonu (WPF Yönetilmeyen API Başvurusu)
Bu API, Windows Sunu Temeli (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.  
  
 İş parçacığı ve windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parametreler  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 pDispatchTemsilcisi  
 `IDispatch` Arabirime işaretçi.  
  
 ppForwarder  
 `IDispatch` Arabirimin adresine işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [.NET Çerçeve Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve sonraki olarak: PresentationHost_v0400.dll  
  
 **.NET Çerçeve Sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
