---
title: Veri Sözleşmesi Eşitliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: b96a32f5e11ed4808f8f35d02802afd1f48c3072
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601328"
---
# <a name="data-contract-equivalence"></a>Veri Sözleşmesi Eşitliği
Bir istemcinin belirli bir türdeki verileri bir hizmete veya bir istemciye başarıyla veri göndermek için bir hizmete başarıyla göndermesini sağlamak için, gönderilen türün alma sonunda bulunması gerekmez. Tek gereksinim, her iki türdeki veri sözleşmelerinin de aynı olması olabilir. (Bazen, [veri anlaşması sürümü oluşturma](data-contract-versioning.md)bölümünde açıklandığı gibi katı denklik gerekli değildir.)  
  
 Veri sözleşmelerinin eşdeğer olması için aynı ad alanına ve ada sahip olmaları gerekir. Ayrıca, bir taraftaki her bir veri üyesinin diğer tarafta eşdeğer bir veri üyesi olması gerekir.  
  
 Veri üyelerinin eşit olması için aynı ada sahip olmaları gerekir. Ayrıca, aynı türde verileri temsil etmelidir; diğer bir deyişle, veri sözleşmeleri eşdeğer olmalıdır.  
  
> [!NOTE]
> Veri sözleşmesi adlarının ve ad alanlarının yanı sıra veri üyesi adlarının büyük/küçük harfe duyarlı olduğunu unutmayın.  
  
 Veri sözleşmesi adları ve ad alanları ve veri üyesi adları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](data-contract-names.md).  
  
 Aynı tarafta (Gönderen veya alıcı) iki tür varsa ve veri sözleşmeleri eşit değildir (örneğin, farklı veri üyeleri varsa), bunlara aynı ad ve ad alanı vermemelisiniz. Bunun yapılması özel durumların oluşturulmasına neden olabilir.  
  
 Aşağıdaki türler için veri sözleşmeleri eşdeğerdir:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Veri üyesi siparişi ve veri sözleşmesi denklik  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>Sınıfının özelliğinin kullanılması, <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşmesinin denkdeğerliğine etkilenebilir. Veri sözleşmeleri, eşdeğer olması için aynı sırada görünen üyelere sahip olmalıdır. Varsayılan sıra alfabetik bir değer. Daha fazla bilgi için bkz. [veri üye sıralaması](data-member-order.md).  
  
 Örneğin, aşağıdaki kod eşdeğer veri sözleşmeleri ile sonuçlanır.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ancak, aşağıdakiler eşdeğer bir veri sözleşmesine neden olmaz.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Devralma, arabirimler ve veri sözleşmesi denklik  
 Denklik belirlenirken, başka bir veri sözleşmesinden devralan bir veri sözleşmesi, temel türden tüm veri üyelerini içeren yalnızca bir veri anlaşması gibi değerlendirilir. Veri üyeleri sırasının eşleşmesi gerektiğini ve temel tür üyelerinin, türetilmiş tür üyelerinden önce sipariş olarak gelmesini aklınızda bulundurun. Ayrıca, aşağıdaki kod örneğinde olduğu gibi, iki veri üyesinin aynı sıra değeri varsa, bu veri üyeleri için sıralama alfabetik bir örnektir. Daha fazla bilgi için bkz. [veri üye sıralaması](data-member-order.md).  
  
 Aşağıdaki örnekte, türü için veri sözleşmesi, `Employee` türü için veri sözleşmesine eşdeğerdir `Worker` .  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Parametreler ve bir istemci ile bir hizmet arasında değer döndürerdiğinde, alıcı uç nokta türetilmiş bir sınıftan bir veri anlaşması beklerken, taban sınıftan bir veri sözleşmesi gönderilemez. Bu, nesne odaklı programlama tenetleri 'ne uygun. Önceki örnekte, türünde bir nesne `Person` `Employee` beklendiğinde gönderilemez.  
  
 Türetilmiş bir sınıftan veri sözleşmesi, bir temel sınıftan veri sözleşmesi beklendiğinde, ancak yalnızca ' ı kullanarak türetilmiş türün "biliyor" ise gönderilebilir <xref:System.Runtime.Serialization.KnownTypeAttribute> . Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md). Önceki örnekte, `Employee` bir nesne `Person` beklendiğinde, ancak yalnızca alıcı kodu <xref:System.Runtime.Serialization.KnownTypeAttribute> onu bilinen türler listesine eklemek için kullanıyorsa, türü bir nesnesi gönderilebilir.  
  
 Parametreler ve uygulamalar arasında dönüş değerlerini geçirdiğinde, beklenen tür bir arabirimiyorsa, tür olan beklenen tür ile eşdeğerdir <xref:System.Object> . Her tür son olarak öğesinden türetildiğinden <xref:System.Object> , her ne kadar veri sözleşmesi için veri sözleşmesinden türetilir <xref:System.Object> . Bu nedenle, bir arabirim beklendiğinde herhangi bir veri anlaşması türü geçirilebilir. Arabirimler ile başarılı bir şekilde çalışmak için ek adımlar gereklidir; daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Üye Sırası](data-member-order.md)
- [Veri Anlaşması Bilinen Türler](data-contract-known-types.md)
- [Veri Sözleşmesi Adları](data-contract-names.md)
