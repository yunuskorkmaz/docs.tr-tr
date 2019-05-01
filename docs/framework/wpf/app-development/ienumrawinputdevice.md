---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949571"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Bu arabirim, ham giriş cihazları numaralandırır ve yalnızca PresentationHost.exe tarafından kullanılır.  
  
> [!NOTE]
>  Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Sonraki numaralandırır `celt` numaralandırıcı listesi olarak (diğer bir deyişle, RAWINPUTDEVICE yapıları) öğelerinde `rgelt` numaralandırılmış öğelerinde gerçek sayısını `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Sonraki Numaralandırıcıya bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) bu öğeleri döndürmez.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Sabit listesi sırası başlangıç durumuna sıfırlar.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Aynı liste üzerinde yineleme yapmak için geçerli bir numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazının Numaralandırıcı oluşturur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ham giriş hakkında](/windows/desktop/inputdev/about-raw-input)
