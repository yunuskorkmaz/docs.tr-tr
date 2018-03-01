---
title: ISymUnmanagedDocument Arabirimi
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
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument Arabirimi
Sembol deposu tarafından başvurulan bir belgeyi temsil eder. Bir belgeyi bir Tekdüzen Kaynak Konum Belirleyicisi (URL) ve bir belge türü GUID tarafından tanımlanır. URL'yi kullanarak nasıl depolanacağını bağımsız olarak belgeyi bulun ve belge türü GUID. Belge kaynağı simgesi deposunda depola ve bu arabirimi aracılığıyla alın.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindClosestLine Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Bir satır olabilir veya bir dizi noktası olmayabilir bu belgede verilen bir dizi noktası en yakın satır döndürür.|  
|[GetCheckSum Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Sağlama toplamı alır.|  
|[GetCheckSumAlgorithmId Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı ise sıfırlardan GUİD'si döndürür.|  
|[GetDocumentType Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Bu belgenin belge türünü alır.|  
|[GetLanguage Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Bu belge dil tanımlayıcısını alır.|  
|[GetLanguageVendor Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Bu belgenin dil satıcı alır.|  
|[GetSourceLength Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Katıştırılmış kaynak bayt cinsinden uzunluğu alır.|  
|[GetSourceRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Katıştırılmış kaynak belirtilen aralığını verilen arabelleğe döndürür.|  
|[GetURL Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Bu belge için URL'yi döndürür.|  
|[HasEmbeddedSource Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Döndürür `true` hata ayıklama simgeleri; katıştırılmış kaynak belge varsa, aksi takdirde, döndürür `false`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
