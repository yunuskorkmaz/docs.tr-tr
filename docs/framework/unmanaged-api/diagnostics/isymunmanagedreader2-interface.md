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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 890053e1bf2e0648a41cca718e94edcf21c7e612
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986225"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 Arabirimi
Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder. Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Bir sembol okuyucu yöntemi verilen token metody ve bir Düzenle ve devam et sürüm numarasını alın.|  
|[GetMethodsInDocument Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Sağlanan belge içinde satır bilgileri her yöntemin alır.|  
|[GetSymAttributePreRemap Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Özel bir öznitelik adı üzerinde temel alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
