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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615572"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument Arabirimi
Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder. Belge, Tekdüzen Kaynak Bulucu (URL) ve belge türü GUID 'SI tarafından tanımlanır. Belgeyi, URL ve belge türü GUID kullanılarak nasıl depolandığına bakılmaksızın bulabilirsiniz. Belge kaynağını sembol deposunda depolayıp bu arabirim aracılığıyla alabilirsiniz.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindClosestLine Yöntemi](isymunmanageddocument-findclosestline-method.md)|Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.|  
|[GetCheckSum Yöntemi](isymunmanageddocument-getchecksum-method.md)|Sağlama toplamını alır.|  
|[GetCheckSumAlgorithmId Yöntemi](isymunmanageddocument-getchecksumalgorithmid-method.md)|Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı yoksa tüm sıfırları GUID 'leri döndürür.|  
|[GetDocumentType Yöntemi](isymunmanageddocument-getdocumenttype-method.md)|Bu belgenin belge türünü alır.|  
|[GetLanguage Yöntemi](isymunmanageddocument-getlanguage-method.md)|Bu belgenin dil tanımlayıcısını alır.|  
|[GetLanguageVendor Yöntemi](isymunmanageddocument-getlanguagevendor-method.md)|Bu belgenin dil satıcısını alır.|  
|[GetSourceLength Yöntemi](isymunmanageddocument-getsourcelength-method.md)|Gömülü kaynağın uzunluğunu bayt olarak alır.|  
|[GetSourceRange Yöntemi](isymunmanageddocument-getsourcerange-method.md)|Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür.|  
|[GetURL Yöntemi](isymunmanageddocument-geturl-method.md)|Bu belgenin URL 'sini döndürür.|  
|[HasEmbeddedSource Yöntemi](isymunmanageddocument-hasembeddedsource-method.md)|`true`Belgenin hata ayıklama sembollerine katıştırılmış kaynak olup olmadığını döndürür; Aksi takdirde, döndürür `false` .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
