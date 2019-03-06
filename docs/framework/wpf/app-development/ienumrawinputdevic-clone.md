---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: a4c5e7db813089d1dd138416ac54dd4be467b87b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355028"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Aynı liste üzerinde yineleme yapmak için geçerli bir numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazının Numaralandırıcı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppenum`  
  
 [out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) arabirim işaretçisi. Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımsızdır.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Bu yöntem standart dönüş değerleri E_INVALIDARG E_OUTOFMEMORY ve E_UNEXPECTED destekler.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, daha sonra o noktaya döndürmek için numaralandırma sıralı bir nokta kaydetmek mümkün kılar. Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak yayınlamanız gerekir.
