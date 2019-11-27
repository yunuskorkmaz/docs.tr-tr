---
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
ms.openlocfilehash: 20556d85655a0a1bbe069a94b99c19c774a13ce6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449686"
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
 dışı İşlemdeki çalışan bir CLR örneğinin temsili KIMLIĞI. Bu, Windows için olay izleme (ETW) başlatma olayı raporlarının `ClrInstanceID` aynıdır.  
  
 `pRuntimeType`  
 dışı Çalışma zamanı türü. Bu parametre, CLR 'nin masaüstü sürümü için `COR_PRF_DESKTOP_CLR` veya Silverlight 'ta kullanılan CLR 'nin çekirdek sürümü için `COR_PRF_CORE_CLR` döndürür.  
  
 `pMajorVersion`  
 dışı CLR 'nin ana sürüm numarası.  
  
 `pMinorVersion`  
 dışı CLR 'nin ikincil sürüm numarası.  
  
 `pBuildVersion`  
 dışı CLR 'nin derleme sürüm numarası.  
  
 `pQFEVersion`  
 dışı Bir yazılım güncelleştirmesiyle ilişkilendirilen CLR 'nin sürüm numarası.  
  
 `cchVersionString`  
 'ndaki `szVersionString` arabelleğin gösterdiği uzunluğun uzunluğu (karakter).  
  
 `pcchVersionString`  
 dışı `szVersionString`karakter cinsinden uzunluğu.  
  
 `szVersionString`  
 dışı CLR sürüm dizesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir parametre için null değeri geçirebilirsiniz. Ancak, `szVersionString` da null olmadığı müddetçe `pcchVersionString` null olamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
