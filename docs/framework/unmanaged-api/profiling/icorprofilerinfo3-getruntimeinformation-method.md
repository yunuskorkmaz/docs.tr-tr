---
title: ICorProfilerInfo3::GetRuntimeInformation Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetRuntimeInformation Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eadd9970d29cc65d8411692407dcae5471e51c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation Metodu
Profili oluşturuluyor ortak dil çalışma zamanı (CLR) sürüm bilgilerini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pClrInstanceId`  
 [out] Bir işlemde çalışan bir CLR örneği temsilcisi kimliği. Bu aynı sonucu verir `ClrInstanceID` Windows (ETW) başlangıç olayı için olay izleme raporları.  
  
 `pRuntimeType`  
 [out] Çalışma zamanı türü. Bu parametre döndürür `COR_PRF_DESKTOP_CLR` Masaüstü CLR sürümü için veya `COR_PRF_CORE_CLR` Silverlight'ta kullanılan CLR çekirdek sürümü.  
  
 `pMajorVersion`  
 [out] CLR ana sürüm numarası.  
  
 `pMinorVersion`  
 [out] CLR ikincil sürüm numarası.  
  
 `pBuildVersion`  
 [out] CLR derleme sürüm numarası.  
  
 `pQFEVersion`  
 [out] Bir yazılım güncelleştirmesiyle ilişkili CLR sürüm numarası.  
  
 `cchVersionString`  
 [in] Arabellek karakter cinsinden uzunluğu, `szVersionString` işaret eder.  
  
 `pcchVersionString`  
 [out] Karakter cinsinden uzunluğu, `szVersionString`.  
  
 `szVersionString`  
 [out] CLR sürüm dizesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Her parametre için null iletebilir. Ancak, `pcchVersionString` null olamaz sürece `szVersionString` de NULL'dur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
