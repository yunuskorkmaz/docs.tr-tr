---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545355"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Aynı liste üzerinde yinelemek için geçerli Numaralandırıcı ile aynı duruma sahip başka bir ham giriş aygıt numaralandırıcısı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppenum`  
  
 [out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) arabirim işaretçisi. Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımlanmamıştır.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Bu yöntem E_INVALIDARG, E_OUTOFMEMORY ve E_UNEXPECTED standart dönüş değerlerini destekler.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem daha sonraki bir zamanda bu noktaya kadar dönebilmek için numaralandırma sırayla bir noktası kaydetmek mümkün kılar. Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak serbest bırakmanız gerekir.
