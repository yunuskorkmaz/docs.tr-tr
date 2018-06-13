---
title: ISymUnmanagedENCUpdate Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05cbe098b73dd817546dd72f0fc98ad548f75386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425424"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate Arabirimi
Düzenle ve devam et özelliği işlevleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetLocalVariableCount Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Yerel değişkenler sayısını alır.|  
|[GetLocalVariables Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Yerel değişkenler alır.|  
|[InitializeForEnc Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Önce ilk çağrıda hesaplanacak yöntemi sınırları verir [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.|  
|[UpdateMethodLines Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Değil derlendikten ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgilerin güncelleştirilmesini sağlar. Her deyim için bir delta izin verilir.|  
|[UpdateSymbolStore2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılayan koşuluyla atlamak bir derleyici sağlar. Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
