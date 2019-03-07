---
title: ICorDebugMetaDataLocator::GetMetaData Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c787a93ac98a086dfb6218d1b4891de87e0e107d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487009"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData Metodu
Tam yolu, meta veri hata ayıklayıcı istenen bir işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszImagePath`  
 [in] Dosyaya tam yolunu temsil ettiği bir null ile sonlandırılmış bir dize. Tam yol mevcut değilse adı ve dosya uzantısını (*filename*. *Uzantı*).  
  
 `dwImageTimeStamp`  
 [in] Görüntünün PE dosyası başlıklarından zaman damgası. Bu parametre için bir sembol sunucusu potansiyel olarak kullanılabilir ([SymSrv](/windows/desktop/debug/using-symsrv)) araması.  
  
 `dwImageSize`  
 [in] PE dosyası başlıklarından resim boyutu. Bu parametre, büyük olasılıkla SymSrv arama için kullanılabilir.  
  
 `cchPathBuffer`  
 [in] Karakter sayısında `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Sayısı `WCHAR`yazılan s `wszPathBuffer`.  
  
 Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, sayısı içeren `WCHAR`s gereken yolu depolamak.  
  
 `wszPathBuffer`  
 [out] İçine istenen meta verilerini içeren dosyanın tam yolunu hata ayıklayıcı kopyalayacak bir arabellek için işaretçi.  
  
 `ofReadOnly` Gelen bayrak [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırma meta verileri bu dosyada salt okunur erişim istemek için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar. Diğer tüm başarısız HRESULTs dosya alınabilir olduğunu gösterir.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı. `wszPathBuffer` dosyanın tam yolunu içerir ve null sonlandırılmıştır.|  
|E_NOT_SUFFICIENT_BUFFER|Geçerli boyutunu `wszPathBuffer` tam yolunu tutmak yeterli değil. Bu durumda, `pcchPathBuffer` gerekli sayısı içeren `WCHAR`s, sonlandırıcı null karakter de dahil olmak üzere ve `GetMetaData` istenen arabellek boyutu ile ikinci kez çağrılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `wszImagePath` tam yolu içeren isteğe bağlı olarak bir modülden için bir döküm, döküm burada toplanmıştır bilgisayardan yolunu belirtir. Dosyanın bu konumda mevcut değil veya yanlış bir dosya aynı ada sahip yol üzerinde depolanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
