---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod arabirimi'
title: ISymUnmanagedMethod Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 18f87784a959ddc62415592e51d1971ea10f90bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709964"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod Arabirimi

Sembol deposu içindeki bir yöntemi temsil eder. Bu arabirim, türle ilgili öznitelikler yerine yalnızca bir yöntemin sembolüyle ilgili özniteliklerine erişim sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetNamespace Yöntemi](isymunmanagedmethod-getnamespace-method.md)|Bu yöntemin tanımlandığı ad alanını alır.|  
|[GetOffset Yöntemi](isymunmanagedmethod-getoffset-method.md)|Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.|  
|[GetParameters Yöntemi](isymunmanagedmethod-getparameters-method.md)|Bu yöntemin parametrelerini alır.|  
|[GetRanges Yöntemi](isymunmanagedmethod-getranges-method.md)|Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.|  
|[GetRootScope Yöntemi](isymunmanagedmethod-getrootscope-method.md)|Bu metot içindeki kök sözcük kapsamını alır. Bu kapsam tüm yöntemi barındırır.|  
|[GetScopeFromOffset Yöntemi](isymunmanagedmethod-getscopefromoffset-method.md)|Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.|  
|[GetSequencePointCount Yöntemi](isymunmanagedmethod-getsequencepointcount-method.md)|Bu yöntemin içindeki sıra noktalarının sayısını alır.|  
|[GetSequencePoints Yöntemi](isymunmanagedmethod-getsequencepoints-method.md)|Bu yöntemin içindeki tüm sıra noktalarını alır.|  
|[GetSourceStartEnd Yöntemi](isymunmanagedmethod-getsourcestartend-method.md)|Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.|  
|[GetToken Metodu](isymunmanagedmethod-gettoken-method.md)|Bu yöntem için meta veri belirtecini döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
