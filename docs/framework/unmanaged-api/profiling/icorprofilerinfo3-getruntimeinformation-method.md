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
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496405"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation Metodu
Profili oluşturulan ortak dil çalışma zamanı (CLR) hakkında sürüm bilgileri sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
