---
title: FilterInputMessage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b3a0e58c7485d46f004db7ea52215be60340b68
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="filterinputmessage"></a>FilterInputMessage
E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMsg`  
  
 [in] Ham giriş alma penceresine WM_INPUT iletisi gönderdi.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT:  
  
 S_OK - filtre iletiyi işlemedi ve başka bir işleme ortaya çıkabilir.  
  
 S_FALSE - filtre bu ileti işleme ve başka işlem olmamalıdır.  
  
 Bu değeri döndürülürse, E_NOTIMPL – [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) yeniden çağrılmaz. Bu yalnızca özel ilerleme sağlanmasıyla ilgilenen bir konak uygulamasından döndürülen ve hata kullanıcı arabirimlerinin PresentationHost.exe değil ilgileniyor ham giriş iletilerini PresentationHost.exe iletilen.  
  
## <a name="remarks"></a>Açıklamalar  
 PresentationHost.exe klavye, fare ve Uzaktan denetimler de dahil olmak üzere çeşitli ham giriş aygıtlarının hedefidir. Bazı durumlarda, ana bilgisayar uygulamasını davranışını PresentationHost.exe tarafından tüketilen giriş bağımlıdır. Örneğin, bir ana bilgisayar uygulaması belirli kullanıcı arabirimi öğeleri kullanılıp kullanılmayacağını belirlemek için belirli giriş iletilerinin alınmasına bağlı olabilir.  
  
 Ana bilgisayar uygulamasının bu davranışların sağlamak için gerekli giriş iletilerini almasına izin vermek için PresentationHost.exe barındırılan uygulama için uygun ham giriş iletilerini çağırarak iletir [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 Barındırılan uygulama tarafından döndürülen ham giriş aygıtları (İnsan Arabirimi aygıtları) kümesi ile kaydederek ham giriş iletilerini alır [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WM_INPUT Bildirimi](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
