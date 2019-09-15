---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991753"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
  
 dışı Ham giriş cihazlarını numaralandırmak için bir [ıenumoywınputdevice](ienumrawinputdevice.md) işaretçisi.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT  
  
 S_OK- [ıenumkıwınputdevice](ienumrawinputdevice.md) yalnızca S_OK döndürülürse, PresentationHost. exe tarafından kullanılır.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Açıklamalar  
 Ham giriş aygıtları, uzaktan kumandalar gibi klavye, fare ve daha az geleneksel cihazları içeren giriş cihazlarıdır.  
  
 Ham giriş cihazlarının listesi alındıktan sonra PresentationHost. exe, WM_INPUT bildirim iletilerini almak için cihazlara kaydolur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Getpwınputdevicelist](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
