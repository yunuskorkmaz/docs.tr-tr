---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerInfo3:: GetRuntimeInformation yöntemi'
title: ICorProfilerInfo3::GetRuntimeInformation Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: f615cc54e12b6f2f6eaa7335353f2f5f6a8ecfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646718"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation Metodu

Profili oluşturulan ortak dil çalışma zamanı (CLR) hakkında sürüm bilgileri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  

 `pClrInstanceId`  
 dışı İşlemdeki çalışan bir CLR örneğinin temsili KIMLIĞI. Bu, `ClrInstanceID` Windows için olay izleme (ETW) başlatma olay raporlarıdır.  
  
 `pRuntimeType`  
 dışı Çalışma zamanı türü. Bu parametre `COR_PRF_DESKTOP_CLR` , clr 'nin masaüstü sürümü veya `COR_PRF_CORE_CLR` Silverlight 'DA kullanılan CLR 'nin çekirdek sürümü için döndürür.  
  
 `pMajorVersion`  
 dışı CLR 'nin ana sürüm numarası.  
  
 `pMinorVersion`  
 dışı CLR 'nin ikincil sürüm numarası.  
  
 `pBuildVersion`  
 dışı CLR 'nin derleme sürüm numarası.  
  
 `pQFEVersion`  
 dışı Bir yazılım güncelleştirmesiyle ilişkilendirilen CLR 'nin sürüm numarası.  
  
 `cchVersionString`  
 'ndaki ' I işaret eden arabelleğin karakter cinsinden uzunluğu `szVersionString` .  
  
 `pcchVersionString`  
 dışı Karakter cinsinden uzunluğu `szVersionString` .  
  
 `szVersionString`  
 dışı CLR sürüm dizesi.  
  
## <a name="remarks"></a>Açıklamalar  

 Herhangi bir parametre için null değeri geçirebilirsiniz. Ancak `pcchVersionString` aynı zamanda null olmadığı için null olamaz `szVersionString` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
