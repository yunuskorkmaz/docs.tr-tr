---
title: ISymUnmanagedWriter::CloseMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: fcf250f10baf4c65cd1c8c918655e4b9f4f5cc4b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731741"
---
# <a name="isymunmanagedwriterclosemethod-method"></a>ISymUnmanagedWriter::CloseMethod Yöntemi

Geçerli yöntemi kapatır. Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [OpenMethod Yöntemi](isymunmanagedwriter-openmethod-method.md)
