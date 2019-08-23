---
title: Veri Sözleşmesi Eşitliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: 448c47d8687aa32671ade016f9b48cd763f87dfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945358"
---
# <a name="data-contract-equivalence"></a>Veri Sözleşmesi Eşitliği
Bir istemcinin belirli bir türdeki verileri bir hizmete veya bir istemciye başarıyla veri göndermek için bir hizmete başarıyla göndermesini sağlamak için, gönderilen türün alma sonunda bulunması gerekmez. Tek gereksinim, her iki türdeki veri sözleşmelerinin de aynı olması olabilir. (Bazen, [veri anlaşması sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)bölümünde açıklandığı gibi katı denklik gerekli değildir.)  
  
 Veri sözleşmelerinin eşdeğer olması için aynı ad alanına ve ada sahip olmaları gerekir. Ayrıca, bir taraftaki her bir veri üyesinin diğer tarafta eşdeğer bir veri üyesi olması gerekir.  
  
 Veri üyelerinin eşit olması için aynı ada sahip olmaları gerekir. Ayrıca, aynı türde verileri temsil etmelidir; diğer bir deyişle, veri sözleşmeleri eşdeğer olmalıdır.  
  
> [!NOTE]
> Veri sözleşmesi adlarının ve ad alanlarının yanı sıra veri üyesi adlarının büyük/küçük harfe duyarlı olduğunu unutmayın.  
  
 Veri sözleşmesi adları ve ad alanları ve veri üyesi adları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Aynı tarafta (Gönderen veya alıcı) iki tür varsa ve veri sözleşmeleri eşit değildir (örneğin, farklı veri üyeleri varsa), bunlara aynı ad ve ad alanı vermemelisiniz. Bunun yapılması özel durumların oluşturulmasına neden olabilir.  
  
 Aşağıdaki türler için veri sözleşmeleri eşdeğerdir:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Veri üyesi siparişi ve veri sözleşmesi denklik  
 Sınıfının<xref:System.Runtime.Serialization.DataMemberAttribute> özelliğinin <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> kullanılması, veri sözleşmesinin denkdeğerliğine etkilenebilir. Veri sözleşmeleri, eşdeğer olması için aynı sırada görünen üyelere sahip olmalıdır. Varsayılan sıra alfabetik bir değer. Daha fazla bilgi için bkz. [veri üye sıralaması](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Örneğin, aşağıdaki kod eşdeğer veri sözleşmeleri ile sonuçlanır.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ancak, aşağıdakiler eşdeğer bir veri sözleşmesine neden olmaz.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Devralma, arabirimler ve veri sözleşmesi denklik  
 Denklik belirlenirken, başka bir veri sözleşmesinden devralan bir veri sözleşmesi, temel türden tüm veri üyelerini içeren yalnızca bir veri anlaşması gibi değerlendirilir. Veri üyeleri sırasının eşleşmesi gerektiğini ve temel tür üyelerinin, türetilmiş tür üyelerinden önce sipariş olarak gelmesini aklınızda bulundurun. Ayrıca, aşağıdaki kod örneğinde olduğu gibi, iki veri üyesinin aynı sıra değeri varsa, bu veri üyeleri için sıralama alfabetik bir örnektir. Daha fazla bilgi için bkz. [veri üye sıralaması](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, türü `Employee` için veri sözleşmesi, türü `Worker`için veri sözleşmesine eşdeğerdir.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Parametreler ve bir istemci ile bir hizmet arasında değer döndürerdiğinde, alıcı uç nokta türetilmiş bir sınıftan bir veri anlaşması beklerken, taban sınıftan bir veri sözleşmesi gönderilemez. Bu, nesne odaklı programlama tenetleri 'ne uygun. Önceki örnekte, türünde `Person` bir nesne `Employee` beklendiğinde gönderilemez.  
  
 Türetilmiş bir sınıftan veri sözleşmesi, bir temel sınıftan veri sözleşmesi beklendiğinde, ancak yalnızca ' ı kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>türetilmiş türün "biliyor" ise gönderilebilir. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Önceki örnekte, bir `Employee` `Person` nesne beklendiğinde, ancak yalnızca alıcı kodu onu bilinen türler listesine eklemek <xref:System.Runtime.Serialization.KnownTypeAttribute> için kullanıyorsa, türü bir nesnesi gönderilebilir.  
  
 Parametreler ve uygulamalar arasında dönüş değerlerini geçirdiğinde, beklenen tür bir arabirimiyorsa, tür <xref:System.Object>olan beklenen tür ile eşdeğerdir. Her tür son olarak öğesinden türetildiğinden, her ne kadar <xref:System.Object>veri sözleşmesi için <xref:System.Object>veri sözleşmesinden türetilir. Bu nedenle, bir arabirim beklendiğinde herhangi bir veri anlaşması türü geçirilebilir. Arabirimler ile başarılı bir şekilde çalışmak için ek adımlar gereklidir; daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Üye Sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Veri Anlaşması Adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
