---
title: "ISymUnmanagedWriter::DefineSequencePoints Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e1dcc427a6d034ce108ca66f71cc24b1050a72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints Yöntemi
Geçerli yöntemi içinde sıralama noktaları grubunu tanımlar. Her bir başlangıç satırı ve başlangıç sütunu deyimi bir yöntem içinde başlangıcı tanımlayın. Her bitiş satır ve sütun bitiş deyimi bir yöntem içinde sonuna tanımlayın. Diziler uzaklıkları artan düzende sıralanmış. Uzaklık her zaman yönteminin bayt cinsinden ölçülür.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `document`  
 [in] Sıralama noktaları tanımlı belge nesnesi.  
  
 `spCount`  
 [in] A `ULONG32` her birinin boyutunu gösterir, `offsets`, `lines`, `columns`, `endLines`, ve `endColumns` arabellek.  
  
 `offsets`  
 [in] Sıralama noktaları uzaklığını yöntemi başından itibaren ölçülür.  
  
 `lines`  
 [in] Sıralama noktaları başlangıç satır sayısı.  
  
 `columns`  
 [in] Sıralama noktaları başlangıç sütun sayıları.  
  
 `endLines`  
 [in] Sıralama noktaları bitiş satır numaralarını. Bu parametre isteğe bağlıdır.  
  
 `endColumns`  
 [in] Sıralama noktaları bitiş sütun sayıları. Bu parametre isteğe bağlıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
