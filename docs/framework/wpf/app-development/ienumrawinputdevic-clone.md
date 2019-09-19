---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053414"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Aynı listede yinelemek için geçerli numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazı numaralandırıcısı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppenum`  
  
 dışı [Ienumoywınputdevice](ienumrawinputdevice.md) arabirimini alan çıkış değişkeninin adresi. Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımsız olur.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT Bu yöntem, E_INVALIDARG, E_OUTOFMEMORY ve E_UNEXPECTED standart dönüş değerlerini destekler.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, daha sonra bu noktaya geri dönebilmek için numaralandırma dizisine bir nokta kaydetmeyi mümkün hale getirir. Çağıranın bu yeni Numaralandırıcı ilk numaralandırıcıdan ayrı olarak serbest bırakılması gerekir.
