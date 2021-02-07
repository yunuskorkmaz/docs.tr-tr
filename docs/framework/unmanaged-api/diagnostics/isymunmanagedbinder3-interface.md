---
description: 'Daha fazla bilgi edinin: ISymUnmanagedBinder3 Interface'
title: ISymUnmanagedBinder3 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 6d2172fb119076cea6d0f912fb3f403d36856599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689839"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 Arabirimi

Sembol bağlayıcı arabirimini genişletir. Bu arabirimi `QueryInterface` arabirimini uygulayan bir nesne çağırarak edinin `ISymUnmanagedBinder` .  
  
> [!IMPORTANT]
> Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReaderFromCallback Yöntemi](isymunmanagedbinder3-getreaderfromcallback-method.md)|Kullanıcının `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizini bilgilerini elde etmek için bir veya geri çağırma yoluyla veya sağlaması sağlar|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder Arabirimi](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 Arabirimi](isymunmanagedbinder2-interface.md)
