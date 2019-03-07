---
title: ISymUnmanagedWriter::DefineSequencePoints Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4210dedd77c6ab041189fa287e192bb7038080b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491431"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints Yöntemi
Bir dizi noktaları geçerli yöntemi içinde grubunu tanımlar. Her bir başlangıç satırı ve başlangıç sütunu bir ifade bir yöntem içinde başlangıcı tanımlayın. Her bitiş satır ve sütun bitiş sonu bir deyimin bir yöntem içinde tanımlayın. Diziler uzaklıkları artan düzende sıralanmalıdır. Uzaklık her zaman başından itibaren bayt cinsinden yöntemi ölçülür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `document`  
 [in] Dizi noktaları tanımlı belge nesnesi.  
  
 `spCount`  
 [in] A `ULONG32` her birinin boyutunu belirtir `offsets`, `lines`, `columns`, `endLines`, ve `endColumns` arabellek.  
  
 `offsets`  
 [in] Dizi noktaları uzaklığı yöntemi başından itibaren ölçülür.  
  
 `lines`  
 [in] Dizi noktaları başlangıç satır sayısı.  
  
 `columns`  
 [in] Başlangıç sütunu numaralarını sıralama noktaları.  
  
 `endLines`  
 [in] Dizi noktaları bitiş satır numaraları. Bu parametre isteğe bağlıdır.  
  
 `endColumns`  
 [in] Bitiş sütunu numaralarını sıralama noktaları. Bu parametre isteğe bağlıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
