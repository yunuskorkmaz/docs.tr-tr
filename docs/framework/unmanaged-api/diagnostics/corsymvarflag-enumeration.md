---
description: 'Daha fazla bilgi edinin: CorSymVarFlag numaralandırması'
title: CorSymVarFlag Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 28f4b4775e20703e5dcaa7daf69affd3548aa3f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800467"
---
# <a name="corsymvarflag-enumeration"></a>CorSymVarFlag Numaralandırması

Bir değişkenin derleyici tarafından oluşturulup oluşturulmayacağını gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|Verilen değişkenin derleyicinin ürettiği olduğunu gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Numaralandırmaları](diagnostics-symbol-store-enumerations.md)
