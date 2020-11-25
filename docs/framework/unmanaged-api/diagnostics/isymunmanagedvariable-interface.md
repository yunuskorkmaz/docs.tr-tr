---
title: ISymUnmanagedVariable Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 93e1f8eb17f06e42ddb243f88c593979fcb28030
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733288"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable Arabirimi

Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAddressField1 Yöntemi](isymunmanagedvariable-getaddressfield1-method.md)|Bu değişken için ilk adres alanını alır. Bunun anlamı, adresin türüne bağlıdır.|  
|[GetAddressField2 Yöntemi](isymunmanagedvariable-getaddressfield2-method.md)|Bu değişken için ikinci adres alanını alır. Bunun anlamı, adresin türüne bağlıdır.|  
|[GetAddressField3 Yöntemi](isymunmanagedvariable-getaddressfield3-method.md)|Bu değişken için üçüncü adres alanını alır. Bunun anlamı, adresin türüne bağlıdır.|  
|[GetAddressKind Yöntemi](isymunmanagedvariable-getaddresskind-method.md)|Bu değişkenin adres türünü alır.|  
|[GetAttributes Yöntemi](isymunmanagedvariable-getattributes-method.md)|Bu değişken için öznitelik bayraklarını alır.|  
|[GetEndOffset Yöntemi](isymunmanagedvariable-getendoffset-method.md)|Bu değişkenin üst sapmasını üst öğesi içinde alır.|  
|[GetName Yöntemi](isymunmanagedvariable-getname-method.md)|Bu değişkenin adını alır.|  
|[GetSignature Metodu](isymunmanagedvariable-getsignature-method.md)|Bu değişkenin imzasını alır.|  
|[GetStartOffset Yöntemi](isymunmanagedvariable-getstartoffset-method.md)|Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
