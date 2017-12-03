---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
