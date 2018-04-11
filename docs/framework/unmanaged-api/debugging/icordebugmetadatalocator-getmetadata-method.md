---
title: ICorDebugMetaDataLocator::GetMetaData Metodu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4883ee56c7dd027f053dd072d7c8613f606ff2be
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData Metodu
Tam yolu, meta veri hata ayıklayıcı istenen işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı sorar.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `wszImagePath`  
 [in] Dosyaya tam yolunu gösteren bir null ile sonlandırılmış bir dize. Tam yol kullanılabilir değilse adı ve dosya uzantısını (*filename*. *Uzantı*).  
  
 `dwImageTimeStamp`  
 [in] Resmin PE dosya başlıklarından zaman damgası. Bu parametre için bir simge sunucusu potansiyel olarak kullanılabilir ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) arama.  
  
 `dwImageSize`  
 [in] Görüntü boyutu PE dosya başlıklarından. Bu parametre için bir SymSrv arama potansiyel olarak kullanılabilir.  
  
 `cchPathBuffer`  
 [in] Karakter sayısı `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Sayısı `WCHAR`yazılan s `wszPathBuffer`.  
  
 Yöntem E_NOT_SUFFICIENT_BUFFER döndürüyorsa sayısını içeren `WCHAR`s gerekli yolun depolamak.  
  
 `wszPathBuffer`  
 [out] İşaretçi arabellek için istenen meta verilerini içeren dosyanın tam yolunu içine hata ayıklayıcı kopyalayacak.  
  
 `ofReadOnly` Gelen bayrak [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması bu dosyadaki meta veriler salt okunur erişim istemek için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar. Diğer tüm hata HRESULTs dosyası alınabilir olmadığını gösterir.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı. `wszPathBuffer` sonlandırılmış ve dosyanın tam yolunu içerir.|  
|E_NOT_SUFFICIENT_BUFFER|Geçerli boyutunu `wszPathBuffer` tam yolunu tutmak yeterli değil. Bu durumda, `pcchPathBuffer` gerekli sayısını içeren `WCHAR`sonlandırma null karakteri de dahil olmak üzere s ve `GetMetaData` istenen arabellek boyutuna sahip ikinci bir kez çağrılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `wszImagePath` tam bir yol içeriyor isteğe bağlı olarak bir modülden için bir döküm, burada döküm toplandı bilgisayardan yolunu belirtir. Dosyanın bu konumda var olmayabilir veya aynı ada sahip yanlış bir dosya yolunda depolanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
