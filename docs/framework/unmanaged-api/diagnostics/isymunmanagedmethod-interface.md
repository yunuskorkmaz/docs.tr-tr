---
title: ISymUnmanagedMethod Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod
helpviewer_keywords: ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 030ea4b472f6a6aead307e0c5cc94dfb34c19992
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod Arabirimi
Sembol deposu içinde yöntemi temsil eder. Bu arabirim türü ile ilgili öznitelikleri yerine bir yöntemin yalnızca simgesi ilgili öznitelikleri erişim sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetNamespace yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Bu yöntem tanımlandığı ad alır.|  
|[GetOffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Bir belge içinde belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.|  
|[GetParameters yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Bu yöntem için parametre alır.|  
|[GetRanges yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Bir konumda bir belge, bu yöntem içinde konumu kapsayan Microsoft Ara dili (MSIL) aralıklarına karşılık gelir başlangıç ve bitiş uzaklığında çiftleri dizisi döndürür.|  
|[GetRootScope yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Bu yöntem için kök sözcük kapsamda alır. Bu kapsam tüm yöntemi barındırır.|  
|[GetScopeFromOffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözcük kapsamında alır.|  
|[GetSequencePointCount yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Bu yöntem içinde sıralama noktaları sayısını alır.|  
|[GetSequencePoints yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Bu yöntem içindeki tüm sıralama noktaları alır.|  
|[GetSourceStartEnd yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Bu yöntem kaynak için başlangıç ve bitiş belge konumlarına alır.|  
|[GetToken yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Bu yöntem için meta veri belirtecini döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama sembol deposu arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
