---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e936b4ef2cab65e72ca9edbc3b95281815938983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Ana uygulamanın ilgilendiği ham giriş aygıtlarını (İnsan Arabirimi aygıtları) keşfetmek için PresentationHost.exe'ye izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
  
 [out] Bir işaretçi bir [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ham giriş aygıtlarını numaralandırma.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK döndürülürse yalnızca PresentationHost.exe tarafından kullanılır.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Açıklamalar  
 Ham giriş aygıtları klavye, fare ve Uzaktan denetimleri gibi daha az geleneksel aygıtları içeren giriş aygıtları kümesidir.  
  
 Ham giriş aygıtları listesi alındıktan sonra PresentationHost.exe WM_INPUT bildirim iletileri almak için aygıtları kaydeder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
