---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: faf992aa50f8d705caa5f502f61a0fd18cb7ab05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransactionflowgt"></a>&lt;transactionFlow&gt;
Özel bağlama için işlem akışı destek belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<transactionFlow >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|transactionProtocol|Kullanılacak işlem protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> OleTransactions varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, etkinleştirme veya devre dışı bir uç noktanın bağlama ayarları gelen işlem akışında yanı gelen işlemler için istenen protokole biçimi belirtmenizi sağlar. Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokolü, hedef uç nokta herhangi bir iletişim kuralı dışındaki kullanarak yeniden akış denerse işlem zaman aşımı kaybolabilir `OleTransactions`. Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [ServiceModel işlem yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [İşlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
