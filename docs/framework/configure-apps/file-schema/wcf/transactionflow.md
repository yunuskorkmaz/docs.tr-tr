---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8247dd62f4dda853487fe52f00f8f548b627c075
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399392"
---
# <a name="transactionflow"></a>\<transactionFlow >
Özel bağlama için işlem akış desteğini belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|transactionProtocol|Kullanılacak işlem protokolünü belirtir. Geçerli değerler şunlardır:<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Varsayılan değer OleTransactions 'dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar. Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
> Uç noktadan uç `OleTransactions` noktaya işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında `OleTransactions`herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir. Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [ServiceModel İşlem Yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [İşlem Akışını Etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
