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
ms.openlocfilehash: d9269339e8e2ae8d00da701b015aa30cd51cbef3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213380"
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
 'ndaki Dosyanın tam yolunu temsil eden, null ile sonlandırılmış bir dize. Tam yol kullanılamıyorsa dosyanın adı ve uzantısı (*filename*.* Uzantısı*).  
  
 `dwImageTimeStamp`  
 'ndaki Görüntünün PE dosya üst bilgilerindeki zaman damgası. Bu parametre, bir sembol sunucusu ([symsrv](/windows/desktop/debug/using-symsrv)) araması için kullanılabilir.  
  
 `dwImageSize`  
 'ndaki PE dosya başlıklarından görüntü boyutu. Bu parametre, bir SymSrv araması için kullanılabilir.  
  
 `cchPathBuffer`  
 'ndaki İçindeki karakter sayısı `wszPathBuffer` .  
  
 `pcchPathBuffer`  
 dışı `WCHAR`Üzerine yazılan s sayısı `wszPathBuffer` .  
  
 Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, `WCHAR` yolu depolamak için gereken s sayısını içerir.  
  
 `wszPathBuffer`  
 dışı Hata ayıklayıcının istenen meta verileri içeren dosyanın tam yolunu kopyalayabileceği bir arabelleğin işaretçisi.  
  
 `ofReadOnly` [CorOpenFlags](../metadata/coropenflags-enumeration.md) numaralandırmasındaki bayrak, bu dosyadaki meta verilere salt okuma erişimi istemek için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür. Diğer tüm Hata HRESULTs 'ler dosyanın alınabilir olmadığını gösterir.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı. `wszPathBuffer`dosyanın tam yolunu içerir ve null ile sonlandırılır.|  
|E_NOT_SUFFICIENT_BUFFER|Geçerli boyutu `wszPathBuffer` tam yolu tutmak için yeterli değil. Bu durumda, `pcchPathBuffer` `WCHAR` Sonlandırıcı null karakteri dahil olmak üzere gerekli sayısını içerir ve `GetMetaData` İstenen arabellek boyutuyla ikinci bir kez çağırılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `wszImagePath` Modül için bir dökümden tam yol içeriyorsa, dökümün toplandığı bilgisayardan yolu belirtir. Dosya bu konumda bulunmayabilir veya yolda aynı ada sahip yanlış bir dosya depolanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
