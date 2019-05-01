---
title: ISymUnmanagedDocument Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939782"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument Arabirimi
Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder. Bir belge, bir Tekdüzen Kaynak Konum Belirleyicisi (URL) ve bir belge türü GUID ile tanımlanır. URL'yi kullanarak nasıl depolanacağını bağımsız olarak belgeyi bulun ve belge türü GUID. Belge kaynak sembolü deposuna ve bu arabirimi üzerinden alın.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindClosestLine Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Bir dizi noktası olmayabilir veya bu belgeyi bir satır verilen bir dizi noktası en yakın satır döndürür.|  
|[GetCheckSum Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Sağlama toplamı alır.|  
|[GetCheckSumAlgorithmId Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Sağlama algoritması tanımlayıcısını alır veya hiç sağlama toplamı sıfırlardan GUİD'sini döndürür.|  
|[GetDocumentType Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Bu belgenin belge türünü alır.|  
|[GetLanguage Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Bu belgenin dil tanımlayıcısını alır.|  
|[GetLanguageVendor Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Bu belgenin dil satıcı alır.|  
|[GetSourceLength Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Katıştırılmış kaynak bayt cinsinden uzunluğunu alır.|  
|[GetSourceRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Katıştırılmış kaynak Belirtilen aralıktaki belirli arabelleğe döndürür.|  
|[GetURL Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Bu belge için URL'yi döndürür.|  
|[HasEmbeddedSource Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Döndürür `true` hata ayıklama sembolleri; katıştırılmış kaynak belge varsa, aksi halde döndürür `false`.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
