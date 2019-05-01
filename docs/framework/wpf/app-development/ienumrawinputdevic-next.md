---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 05867af48b64cd1898b13fa055859c8cc0367c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949584"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Sonraki numaralandırır `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) numaralandırıcı listesi olarak yapılarda `rgelt` numaralandırılmış öğelerinde gerçek sayısını `pceltFetched`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
  
 [in] Sayısı [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) iade yapıları `rgelt`.  
  
 `rgelt`  
  
 [out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).  
  
 `pceltFetched`  
  
 [out] Aslında sağlanan öğelerin sayısı işaretçisine `rgelt`. Arayan geçirebilir `NULL` varsa `rgelt` biridir.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.
