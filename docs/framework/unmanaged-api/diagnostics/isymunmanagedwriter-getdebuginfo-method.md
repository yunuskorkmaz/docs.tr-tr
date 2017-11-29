---
title: ISymUnmanagedWriter::GetDebugInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Isymunmanagedwriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
