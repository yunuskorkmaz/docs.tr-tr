---
title: ISymUnmanagedWriter::OpenMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610047"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod Yöntemi
Sembol bilgisinin yayıldığını bir yöntem açar. Verilen yöntem, dizi noktalarını, parametreleri ve sözcük temelli kapsamları tanımlamak için çağrılar için geçerli yöntem haline gelir. Tüm yöntem etrafında örtük bir sözcük temelli kapsam vardır. Daha önce kapatılan bir yöntemi yeniden açmak, bu yöntem için önceden tanımlanmış tüm sembolleri siler. Tek seferde yalnızca bir açık yöntem olabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Parametreler  
 `method`  
 'ndaki Açılacak yöntemin meta veri belirteci.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [CloseMethod Yöntemi](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2 Yöntemi](isymunmanagedwriter3-openmethod2-method.md)
