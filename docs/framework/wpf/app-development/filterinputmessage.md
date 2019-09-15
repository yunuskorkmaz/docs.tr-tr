---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1453946766e33843ae9e56f7a7f4dbf1678b81b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991394"
---
# <a name="filterinputmessage"></a>FilterInputMessage
E_NOTIMPL döndürülmediği müddetçe PresentationHost. exe tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a>Parametreler  
 `pMsg`  
  
 'ndaki Ham giriş alan pencereye gönderilen WM_INPUT iletisi.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT  
  
 S_OK-filtre iletiyi işlemedi ve başka işlemler meydana gelebilir.  
  
 S_FALSE-filtre bu iletiyi işledi ve başka bir işleme gerçekleşmemelidir.  
  
 E_NOTIMPL – Bu değer döndürülürse [FilterInputMessage](filterinputmessage.md) yeniden çağrılmaz. Bu, yalnızca özel ilerleme sağlamak isteyen bir konak uygulamasından döndürülebilir ve PresentationHost. exe ' ye yönelik kullanıcı arabirimleri, PresentationHost. exe ' den ham giriş iletileri iletilmek üzere değildir.  
  
## <a name="remarks"></a>Açıklamalar  
 PresentationHost. exe, klavye, fare ve uzak denetimler de dahil olmak üzere çeşitli ham giriş cihazlarının hedefidir. Bazen, ana bilgisayar uygulamasındaki davranış, aksi durumda PresentationHost. exe tarafından tüketilen girişe bağımlıdır. Örneğin, bir konak uygulama belirli kullanıcı arabirimi öğelerinin görüntülenip görüntülenmeyeceğini anlamak için belirli giriş iletilerinin alınmasına bağlı olabilir.  
  
 Konak uygulamasının bu davranışları sağlamak üzere gerekli giriş iletilerini almasına izin vermek için, PresentationHost. exe, [FilterInputMessage](filterinputmessage.md)' ı çağırarak, barındırılan uygulamaya uygun ham giriş iletilerini iletir.  
  
 Barındırılan uygulama, [Getpwınputdevices](getrawinputdevices.md)tarafından döndürülen ham giriş aygıtları (Insan arabirim aygıtları) kümesiyle kaydederek ham giriş iletilerini alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WM_INPUT iletisi](/windows/desktop/inputdev/wm-input)
