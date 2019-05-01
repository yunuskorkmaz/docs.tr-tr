---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949597"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Aynı liste üzerinde yineleme yapmak için geçerli bir numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazının Numaralandırıcı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppenum`  
  
 [out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) arabirim işaretçisi. Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımsızdır.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Bu yöntem standart dönüş değerleri E_INVALIDARG E_OUTOFMEMORY ve E_UNEXPECTED destekler.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, daha sonra o noktaya döndürmek için numaralandırma sıralı bir nokta kaydetmek mümkün kılar. Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak yayınlamanız gerekir.
