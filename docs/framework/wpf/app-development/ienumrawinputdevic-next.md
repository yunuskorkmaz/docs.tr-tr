---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053405"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Numaralandırıcının listesindeki `celt` bir sonraki [çwınputdevice](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) yapılarını sıralar `rgelt` ve bunları içinde numaralandırılmış öğelerin `pceltFetched`gerçek sayısıyla birlikte döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
  
 'ndaki ' De `rgelt`döndürülen [ıwınputdevice](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) yapılarının sayısı.  
  
 `rgelt`  
  
 dışı Numaralandırılmış ıRWıNPUTDEVICE yapılarını almak için bir boyut dizisi (veya daha büyük).  
  
 `pceltFetched`  
  
 dışı Gerçekte içinde `rgelt`sağlanan öğe sayısına yönelik işaretçi. `NULL` Eğer`rgelt` ise, arayan içinde geçiş yapabilir.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT Sağlanan öğe sayısı ise `celt`S_OK; Aksi halde S_FALSE.
