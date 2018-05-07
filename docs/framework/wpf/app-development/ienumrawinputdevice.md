---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 2030ad0ac00419280b45555ff11495c74e4274e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Bu arabirim ham giriş aygıtlarını numaralandırır ve yalnızca PresentationHost.exe tarafından kullanılır.  
  
> [!NOTE]
>  Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|Sonraki numaralandırır `celt` bunları döndüren Numaralandırıcının listesindeki öğeleri (diğer bir deyişle, RAWINPUTDEVICE yapıları) `rgelt` numaralandırılmış öğelerin gerçek sayısını birlikte `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|Sonraki atlamayı Numaralandırıcı bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) bu öğeleri döndürmeyecektir.|  
|[IEnumRAWINPUTDEVIC:Reset](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|Numaralandırma dizisi başına sıfırlar.|  
|[IEnumRAWINPUTDEVIC:Clone](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|Aynı liste üzerinde yinelemek için geçerli Numaralandırıcı ile aynı duruma sahip başka bir ham giriş aygıt numaralandırıcısı oluşturur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RAW girişi hakkında](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
