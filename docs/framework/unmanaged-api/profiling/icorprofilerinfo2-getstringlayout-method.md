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
ms.openlocfilehash: 537840ac03b4136682b78cb964950ab5670a7d7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868622"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout Yöntemi
Bir dize nesnesinin yerleşimi hakkında bilgi alır. Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBufferLengthOffset`  
 dışı Dizenin uzunluğunu depolayan `ObjectID` işaretçisine göre konum uzaklığına yönelik bir işaretçi. Uzunluk bir `DWORD`olarak depolanır.  
  
> [!NOTE]
> Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür. Arabelleğin uzunluğu artık kullanılamıyor.  
  
 `PStringLengthOffset`  
 dışı Konumun, dizenin uzunluğunu depolayan `ObjectID` işaretçisine göre konum uzaklığına yönelik bir işaretçi. Uzunluk bir `DWORD`olarak depolanır.  
  
 `pBufferOffset`  
 dışı Geniş karakter dizesini depolayan `ObjectID` işaretçisine göre arabelleğin uzaklığına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStringLayout` yöntemi, aşağıdakilerin depolandığı konumların `ObjectID` işaretçisine göre uzaklıkları alır:  
  
- Dize arabelleğinin uzunluğu.  
  
- Dizenin kendisi için uzunluğu.  
  
- Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.  
  
 Dizeler null ile sonlandırılmış olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
