---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053370"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Numaralandırıcının, bir sonraki `celt` [ıenumatwınputdevic:](ienumrawinputdevic-next.md) Next çağrısının bu öğeleri döndürmemesi için Numaralandırmadaki bir sonraki öğeleri atlamasını söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
  
 'ndaki Atlanacak öğe sayısı.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT Sağlanan öğe sayısı ise `celt`S_OK; Aksi halde S_FALSE.
