---
title: ISymUnmanagedBinder Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder Arabirimi
Yönetilmeyen kod için bir simge bağlayıcı temsil eder.  
  
> [!IMPORTANT]
>  Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReaderForFile yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak yapısı.|  
|[GetReaderFromStream yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Bir meta veri arabirimi ve sembol deposu içeren bir akışı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> hata ayıklama okuma yapısı belirtilen simge Mağazası'ndan simgeler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama sembol deposu arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Isymunmanagedbinder2 arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [Isymunmanagedbinder3 arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
