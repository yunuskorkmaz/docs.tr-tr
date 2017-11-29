---
title: ISymUnmanagedENCUpdate Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate Arabirimi
Düzenle ve devam et özelliği işlevleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetLocalVariableCount yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Yerel değişkenler sayısını alır.|  
|[GetLocalVariables yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Yerel değişkenler alır.|  
|[Initializeforenc yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Önce ilk çağrıda hesaplanacak yöntemi sınırları verir [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.|  
|[UpdateMethodLines yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Değil derlendikten ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgilerin güncelleştirilmesini sağlar. Her deyim için bir delta izin verilir.|  
|[UpdateSymbolStore2 yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılayan koşuluyla atlamak bir derleyici sağlar. Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama sembol deposu arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
