---
description: ': ICorDebugSymbolProvider arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: bd47f294092ee87fc1f34bc68fe744b447e21f20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659588"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider Arabirimi

Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAssemblyImageBytes Yöntemi](icordebugsymbolprovider-getassemblyimagebytes-method.md)|Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.|  
|[GetAssemblyImageMetadata Yöntemi](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Birleştirilmiş bir derlemeden meta verileri döndürür.|  
|[GetCodeRange Yöntemi](icordebugsymbolprovider-getcoderange-method.md)|Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.|  
|[GetInstanceFieldSymbols Yöntemi](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.|  
|[GetMergedAssemblyRecords Yöntemi](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.|  
|[GetMethodLocalSymbols Yöntemi](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.|  
|[GetMethodParameterSymbols Yöntemi](icordebugsymbolprovider-getmethodparametersymbols-method.md)|Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.|  
|[GetMethodProps Yöntemi](icordebugsymbolprovider-getmethodprops-method.md)|Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.|  
|[GetObjectSize Yöntemi](icordebugsymbolprovider-getobjectsize-method.md)|Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.|  
|[GetStaticFieldSymbols Yöntemi](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|TypeSpec imzasına karşılık gelen statik alan sembollerini alır.|  
|[GetTypeProps Yöntemi](icordebugsymbolprovider-gettypeprops-method.md)|Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
