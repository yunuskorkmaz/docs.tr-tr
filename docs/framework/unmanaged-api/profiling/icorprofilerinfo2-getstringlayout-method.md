---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetStringLayout yöntemi'
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
ms.openlocfilehash: 145d748d756fd30ef0522d1c516f8f63ca604545
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716386"
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
 dışı Dizenin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` . Uzunluk bir olarak depolanır `DWORD` .  
  
> [!NOTE]
> Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür. Arabelleğin uzunluğu artık kullanılamıyor.  
  
 `PStringLengthOffset`  
 dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` . Uzunluk bir olarak depolanır `DWORD` .  
  
 `pBufferOffset`  
 dışı `ObjectID` Geniş karakter dizesini depolayan, işaretçiye göre arabelleğin uzaklığına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetStringLayout`Yöntemi, aşağıdakilerin depolandığı konumların göreli olarak kaydırmalarını alır `ObjectID` :  
  
- Dize arabelleğinin uzunluğu.  
  
- Dizenin kendisi için uzunluğu.  
  
- Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.  
  
 Dizeler null ile sonlandırılmış olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
