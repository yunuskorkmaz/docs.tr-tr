---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 0cb1184ddc3e8051a68dfed12367dea65a06b623
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034506"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Ana bilgisayar uygulaması, ilgileniyor ham giriş cihazlarını (İnsan Arabirimi aygıtları) bulma PresentationHost.exe sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
  
 [out] Bir işaretçi bir [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) için ham giriş cihazları listeleniyor.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK döndürülürse yalnızca PresentationHost.exe tarafından kullanılır.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Açıklamalar  
 Ham giriş cihazları klavye, fare ve daha az geleneksel cihazları uzaktan kumandalar gibi içeren giriş cihazları kümesidir.  
  
 Ham giriş cihazların listesini alındıktan sonra PresentationHost.exe WM_INPUT bildirim iletilerinin alınacağı ile cihazları kaydeder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)  
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
