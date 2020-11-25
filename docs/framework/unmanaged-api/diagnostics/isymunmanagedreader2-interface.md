---
title: ISymUnmanagedReader2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709082"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 Arabirimi

Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder. Bu arabirim [ıstreamunmanagedreader](isymunmanagedreader-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap Yöntemi](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alın.|  
|[GetMethodsInDocument Yöntemi](isymunmanagedreader2-getmethodsindocument-method.md)|Belirtilen belgede satır bilgilerine sahip her yöntemi alır.|  
|[GetSymAttributePreRemap Yöntemi](isymunmanagedreader2-getsymattributepreremap-method.md)|Özel bir özniteliği adına göre alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
