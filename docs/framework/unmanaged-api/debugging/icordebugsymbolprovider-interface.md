---
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: fb947fec8f17fe13374251b4429be798a335eed6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133657"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider Arabirimi
Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAssemblyImageBytes Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.|  
|[GetAssemblyImageMetadata Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Birleştirilmiş bir derlemeden meta verileri döndürür.|  
|[GetCodeRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.|  
|[GetInstanceFieldSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.|  
|[GetMergedAssemblyRecords Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.|  
|[GetMethodLocalSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.|  
|[GetMethodParameterSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.|  
|[GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.|  
|[GetObjectSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.|  
|[GetStaticFieldSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|TypeSpec imzasına karşılık gelen statik alan sembollerini alır.|  
|[GetTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
