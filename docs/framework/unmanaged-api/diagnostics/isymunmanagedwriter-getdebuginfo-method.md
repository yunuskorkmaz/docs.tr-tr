---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: GetDebugInfo yöntemi'
title: ISymUnmanagedWriter::GetDebugInfo Yöntemi
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
ms.openlocfilehash: 2255cc90c0bfcd36dacdf81703af67d3f47739db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762324"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo Yöntemi

Bir derleyicinin taşınabilir yürütülebilir (PE) dosya üstbilgisine hata ayıklama dizini girişini yazması için gereken bilgileri döndürür. Sembol yazıcı, ve hariç tüm alanları doldurur `TimeDateStamp` `PointerToRawData` . (Derleyici, bu iki alanı uygun şekilde ayarlamaktan sorumludur.)  
  
 Bir derleyici bu yöntemi çağırmalıdır, veri blobunu PE dosyasına yayar, IMAGE_DEBUG_DIRECTORY alanı, yayan `PointerToRawData` verileri gösterecek şekilde ayarlayın ve IMAGE_DEBUG_DIRECTORY pe dosyasına yazar. Derleyici Ayrıca `TimeDateStamp` alanı oluşturulan PE dosyasının değerine eşit olacak şekilde ayarlamış olmalıdır `TimeDateStamp` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pIDD`  
 [in, out] Sembol yazıcısının dolduracağı IMAGE_DEBUG_DIRECTORY işaretçisi.  
  
 `cData`  
 'ndaki `DWORD` Hata ayıklama verilerinin boyutunu içeren bir.  
  
 `pcData`  
 dışı `DWORD` Hata ayıklama verilerini içermesi için gereken arabellek boyutunu alan bir işaretçisi.  
  
 `data`  
 dışı Simge deposu için hata ayıklama verilerini tutabilecek kadar büyük bir arabellek işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
