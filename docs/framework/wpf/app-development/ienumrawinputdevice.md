---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964775"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Bu arabirim, ham giriş cihazlarını numaralandırır ve yalnızca PresentationHost. exe tarafından kullanılır.  
  
> [!NOTE]
> Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Numaralandırıcının listesindeki `celt` bir sonraki öğeleri (yani, awınputdevice yapıları) numaralandırdığından, içinde `pceltFetched`numaralandırılmış öğelerin gerçek sayısıyla `rgelt` birlikte döndürür.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Numaralandırıcının, bir sonraki `celt` [ıenumatwınputdevic:](ienumrawinputdevic-next.md) Next çağrısının bu öğeleri döndürmemesi için Numaralandırmadaki bir sonraki öğeleri atlamasını söyler.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Numaralandırma dizisini başlangıca sıfırlar.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Aynı listede yinelemek için geçerli numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazı numaralandırıcısı oluşturur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ham giriş hakkında](/windows/desktop/inputdev/about-raw-input)
