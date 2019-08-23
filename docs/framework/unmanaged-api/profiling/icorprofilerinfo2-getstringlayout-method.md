---
title: ICorProfilerInfo2::GetStringLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963801"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout Yöntemi
Bir dize nesnesinin yerleşimi hakkında bilgi alır. Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBufferLengthOffset`  
 dışı Dizenin uzunluğunu depolayan `ObjectID` işaretçiye göre konum uzaklığına yönelik bir işaretçi. Uzunluk bir `DWORD`olarak depolanır.  
  
> [!NOTE]
> Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür. Arabelleğin uzunluğu artık kullanılamıyor.  
  
 `PStringLengthOffset`  
 dışı Dizenin kendisinin uzunluğunu depolayan `ObjectID` işaretçiye göre konum uzaklığına yönelik bir işaretçi. Uzunluk bir `DWORD`olarak depolanır.  
  
 `pBufferOffset`  
 dışı Geniş karakter dizesini depolayan, `ObjectID` işaretçiye göre arabelleğin uzaklığına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi, aşağıdakilerin depolandığı konumların göreli `ObjectID` olarak kaydırmalarını alır: `GetStringLayout`  
  
- Dize arabelleğinin uzunluğu.  
  
- Dizenin kendisi için uzunluğu.  
  
- Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.  
  
 Dizeler null ile sonlandırılmış olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
