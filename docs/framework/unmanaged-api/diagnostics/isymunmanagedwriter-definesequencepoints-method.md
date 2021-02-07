---
description: 'Hakkında daha fazla bilgi edinin: ı, Esequencepoints yöntemi:D'
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
ms.openlocfilehash: 0c5ac9854ef341512f58cb1cd63ed7dfcde9962e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762337"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints Yöntemi

Geçerli yöntem içindeki bir dizi noktası grubunu tanımlar. Her başlangıç satırı ve başlangıç sütunu, bir yöntem içinde bir deyimin başlangıcını tanımlar. Her bitiş satırı ve bitiş sütunu, bir yöntem içindeki bir deyimin sonunu tanımlar. Dizilerin, uzaklıklarda artan sırada sıralanması gerekir. Konum her zaman yöntemin başından (bayt cinsinden) ölçülür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Sıra noktalarının tanımlandığı belge nesnesi.  
  
 `spCount`  
 'ndaki ,,, `ULONG32` `offsets` `lines` `columns` `endLines` Ve `endColumns` arabelleklerinin her birinin boyutunu belirten bir.  
  
 `offsets`  
 'ndaki Yöntemin başından itibaren ölçülen dizi noktalarının boşluğu.  
  
 `lines`  
 'ndaki Sıra noktalarının başlangıç satırı numaraları.  
  
 `columns`  
 'ndaki Sıra noktalarının başlangıç sütunu numaraları.  
  
 `endLines`  
 'ndaki Sıra noktalarının bitiş çizgisi numaraları. Bu parametre isteğe bağlıdır.  
  
 `endColumns`  
 'ndaki Sıra noktalarının bitiş sütun numaraları. Bu parametre isteğe bağlıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
