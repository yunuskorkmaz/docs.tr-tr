---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: OpenMethod yöntemi'
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
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762233"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod Yöntemi

Sembol bilgisinin yayıldığını bir yöntem açar. Verilen yöntem, dizi noktalarını, parametreleri ve sözcük temelli kapsamları tanımlamak için çağrılar için geçerli yöntem haline gelir. Tüm yöntem etrafında örtük bir sözcük temelli kapsam vardır. Daha önce kapatılan bir yöntemi yeniden açmak, bu yöntem için önceden tanımlanmış tüm sembolleri siler. Tek seferde yalnızca bir açık yöntem olabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
