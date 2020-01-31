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
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793047"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData Metodu
Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Dosyanın tam yolunu temsil eden, null ile sonlandırılmış bir dize. Tam yol kullanılamıyorsa dosyanın adı ve uzantısı (*filename*. *Uzantısı*).  
  
 `dwImageTimeStamp`  
 'ndaki Görüntünün PE dosya üst bilgilerindeki zaman damgası. Bu parametre, bir sembol sunucusu ([symsrv](/windows/desktop/debug/using-symsrv)) araması için kullanılabilir.  
  
 `dwImageSize`  
 'ndaki PE dosya başlıklarından görüntü boyutu. Bu parametre, bir SymSrv araması için kullanılabilir.  
  
 `cchPathBuffer`  
 'ndaki `wszPathBuffer`karakter sayısı.  
  
 `pcchPathBuffer`  
 dışı `wszPathBuffer`yazılan `WCHAR`s sayısı.  
  
 Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, yolu depolamak için gereken `WCHAR`s sayısını içerir.  
  
 `wszPathBuffer`  
 dışı Hata ayıklayıcının istenen meta verileri içeren dosyanın tam yolunu kopyalayabileceği bir arabelleğin işaretçisi.  
  
 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasındaki `ofReadOnly` bayrağı, bu dosyadaki meta verilere salt okuma erişimi istemek için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür. Diğer tüm Hata HRESULTs 'ler dosyanın alınabilir olmadığını gösterir.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı. `wszPathBuffer` dosyanın tam yolunu içerir ve null ile sonlandırılır.|  
|E_NOT_SUFFICIENT_BUFFER|`wszPathBuffer` geçerli boyutu tam yolu tutmak için yeterli değil. Bu durumda `pcchPathBuffer`, Sonlandırıcı null karakteri de dahil olmak üzere gerekli `WCHAR`sayısını içerir ve istenen arabellek boyutuyla `GetMetaData` ikinci bir kez çağrılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `wszImagePath` bir modülden bir modülün tam yolunu içeriyorsa, dökümün toplandığı bilgisayardan yolu belirtir. Dosya bu konumda bulunmayabilir veya yolda aynı ada sahip yanlış bir dosya depolanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
