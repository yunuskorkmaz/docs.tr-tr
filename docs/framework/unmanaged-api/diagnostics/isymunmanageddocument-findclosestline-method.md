---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: FindClosestLine yöntemi'
title: ISymUnmanagedDocument::FindClosestLine Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0409a5cc29bf148a49a5267d34662f763fc302d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737837"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>ISymUnmanagedDocument::FindClosestLine Yöntemi

Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `line`  
 'ndaki Bu belgedeki bir çizgi.  
  
 `pRetVal`  
 dışı Satırı alan bir değişkene yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDocument Arabirimi](isymunmanageddocument-interface.md)
