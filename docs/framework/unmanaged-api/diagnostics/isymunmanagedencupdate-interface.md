---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate arabirimi'
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
ms.openlocfilehash: 4527dfbba840be00cf87a80cdcef3cbde6f275df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721430"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate Arabirimi

Düzenle ve devam et özelliği için işlevler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetLocalVariableCount Yöntemi](isymunmanagedencupdate-getlocalvariablecount-method.md)|Yerel değişkenlerin sayısını alır.|  
|[GetLocalVariables Yöntemi](isymunmanagedencupdate-getlocalvariables-method.md)|Yerel değişkenleri alır.|  
|[InitializeForEnc Yöntemi](isymunmanagedencupdate-initializeforenc-method.md)|Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.|  
|[UpdateMethodLines Yöntemi](isymunmanagedencupdate-updatemethodlines-method.md)|Yeniden derlenmedi ancak satırları bağımsız olarak taşınmış olan bir yöntem için satır bilgilerinin güncelleştirilmesini sağlar. Her ifadeye yönelik bir Delta kullanımına izin verilir.|  
|[UpdateSymbolStore2 Yöntemi](isymunmanagedencupdate-updatesymbolstore2-method.md)|Bir derleyicinin, satır bilgilerinin gereksinimleri karşılaması şartıyla, program veritabanı (PDB) akışından değiştirilmeyen işlevleri yok saymasını sağlar. Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
