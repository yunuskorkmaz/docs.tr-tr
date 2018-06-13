---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546412"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Sonraki numaralandırır `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) yapıları Numaralandırıcının listesi içinde `rgelt` numaralandırılmış öğelerin gerçek sayısını birlikte `pceltFetched`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
  
 [in] Sayısı [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) döndürülen yapıları `rgelt`.  
  
 `rgelt`  
  
 [out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).  
  
 `pceltFetched`  
  
 [out] İşaretçi gerçekte içinde sağlanan öğe sayısı için `rgelt`. Arayan geçirebilir `NULL` varsa `rgelt` biridir.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: sağlanan öğe sayısı ise S_OK `celt`; Aksi durumda S_FALSE.
