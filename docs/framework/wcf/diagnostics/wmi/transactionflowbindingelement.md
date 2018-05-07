---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TransactionFlowBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Verilen güvenlik belirteçleri üstbilgisi (WS-Trust gelen IssuedTokens) gereksinimini belirtir.  
  
### <a name="transactionprotocol"></a>transactionProtocol  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Akış işlemleri için hizmet tarafından kullanılan işlemleri protokol.  
  
### <a name="transactions"></a>İşlemler  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Gelen işlemin desteklenip desteklenmediğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
