---
title: ISymUnmanagedWriter::GetDebugInfo Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1e9a2261ab5fd06e0514efdddf8a8e952a6e3d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo Metodu
Taşınabilir yürütülebilir (PE) dosya üstbilgisinde hata ayıklama dizin girişi yazmak bir derleyici için gerekli bilgileri döndürür. Sembol yazan dışındaki tüm alanları doldurur `TimeDateStamp` ve `PointerToRawData`. (Derleyici, bu iki alan uygun şekilde ayarlamak için sorumlu değildir.)  
  
 Derleyici bu yöntemi çağırın, verileri blob PE dosyaya yayma, Ayarla `PointerToRawData` verilmiş veri noktası ve IMAGE_DEBUG_DIRECTORY PE dosyaya yazmak için IMAGE_DEBUG_DIRECTORY alanındaki. Derleyici de ayarlamalısınız `TimeDateStamp` eşit alan `TimeDateStamp` oluşturulan PE dosyasının.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pIDD`  
 [içinde out] Bir işaretçi simge yazan doldurur bir IMAGE_DEBUG_DIRECTORY için.  
  
 `cData`  
 [in] A `DWORD` hata ayıklama verilerin boyutunu içerir.  
  
 `pcData`  
 [out] Bir işaretçi bir `DWORD` hata ayıklama verileri içerecek şekilde gerekli arabellek boyutunu alır.  
  
 `data`  
 [out] Sembol deposu için hata ayıklama verileri tutmak için yeterince büyük bir arabellek için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
