---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1a22071696ca012968e042e15cd8a9f4b876fd9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479990"
---
# <a name="filterinputmessage"></a>FilterInputMessage
E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMsg`  
  
 [in] WM_INPUT iletisi, işlenmemiş giriş alma pencereye Gönder.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT:  
  
 S_OK - İleti Filtresi işlemedi ve daha fazla işleme ortaya çıkabilir.  
  
 Bu ileti filtresi S_FALSE - işleme ve başka işlem gerçekleşmelidir.  
  
 Bu değer döndürmüyorsa E_NOTIMPL – [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) yeniden çağrılmaz. Bu yalnızca özel ilerleme sağlanmasıyla ilgilenen bir ana bilgisayar uygulaması öğesinden döndürülen ve PresentationHost.exe hata kullanıcı arabirimleri İlgilenmiyor ham giriş iletileri PresentationHost.exe iletilen.  
  
## <a name="remarks"></a>Açıklamalar  
 PresentationHost.exe klavye, fare ve uzak denetimler gibi çeşitli ham giriş cihazlar hedefidir. Bazı durumlarda, ana uygulama davranışını PresentationHost.exe tarafından tüketilen giriş bağlıdır. Örneğin, bir ana bilgisayar uygulaması belirli kullanıcı arabirimi öğeleri görüntülemek gerekip gerekmediğini belirlemek için belirli giriş iletileri almaya üzerinde bağlı olabilir.  
  
 Bu davranışların sağlamak için gerekli giriş iletileri almak ana bilgisayar uygulaması izin vermek için PresentationHost.exe barındırılan uygulama için uygun ham giriş iletileri çağırarak iletir [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 Grup tarafından döndürülen ham giriş cihazı (İnsan Arabirimi cihazları) ile kaydederek barındırılan uygulama ham giriş iletileri alan [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WM_INPUT Bildirimi](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
