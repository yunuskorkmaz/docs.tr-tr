---
title: Veri Sözleşmesi Eşitliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: a526a58ef801e91775756e6a84a94a066d32d284
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214942"
---
# <a name="data-contract-equivalence"></a>Veri Sözleşmesi Eşitliği
Bir istemci başarıyla bir hizmet ya da verileri başarıyla bir istemciye gönderilecek bir hizmeti belirli bir türde veri göndermek gönderilen türü mutlaka alan tarafta mevcut gerekmez. Her iki türdeki veri sözleşmeleri eşdeğer olduğunu tek gereksinim olmasıdır. (Bazı durumlarda, katı denklik bölümünde açıklandığı gibi gerekli değildir [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Veri sözleşmeleri denk olarak bunlar aynı ad alanı ve ad olmalıdır. Ayrıca, her veri üyesi bir tarafta diğer tarafta eşdeğeri veri üyesi olmalıdır.  
  
 Veri üyeleri denk olarak aynı ada sahip olmalıdır. Ayrıca, aynı veri türünü temsil etmelidir; diğer bir deyişle, kendi veri sözleşmeleri eşdeğer olması gerekir.  
  
> [!NOTE]
>  Veri adları ve ad alanları yanı sıra veri üye adları, sözleşme Not büyük küçük harfe duyarlıdır.  
  
 Veri üye adlarının yanı sıra veri sözleşmesi adları ve ad alanları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 İki tür mevcutsa aynı tarafında (gönderen veya alıcı) ve kendi veri anlaşmalar eşdeğer olmadığından (örneğin, farklı veri üyelerinin sahip oldukları), siz bunları aynı ad ve ad vermemelisiniz. Bunun yapılması, özel durum oluşturulmasına neden olabilir.  
  
 Aşağıdaki türler için veri sözleşmeleri eşdeğerdir:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Veri üye sırası ve veri anlaşması eşitliği  
 Kullanarak <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı, veri anlaşması eşitliği etkileyebilir. Veri sözleşmeleri denk olarak aynı sırada görünür üyeleri olmalıdır. Varsayılan olarak alfabetik sıralama kullanılır. Daha fazla bilgi için [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Örneğin, aşağıdaki kod eşdeğeri veri anlaşmalarında sonuçlanır.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ancak, aşağıdaki bir eşdeğeri veri sözleşmede sonuçlanmaz.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Devralma, arabirimler ve veri anlaşması eşitliği  
 Tüm veri üyelerinin temel türünden içeren tek bir veri anlaşması grubundaymış gibi denklik belirlerken, başka bir veri anlaşması devralan bir veri anlaşması kabul edilir. Veri üyelerinin sırasını eşleşmelidir ve temel tür üyeleri koyun, tür üyeleri sırayla türetilmiş aklınızda bulundurun. Aşağıdaki kod örneğinde olduğu gibi iki veri üyeleri aynı sıra değeri varsa, ayrıca, bu veri üyeleri için sıralama alfabetik kullanılır. Daha fazla bilgi için [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, veri anlaşması türü için `Employee` veri anlaşması türü için eşdeğerdir `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Alan uç noktası bir veri anlaşması türetilmiş bir sınıftan beklerken parametrelerini ve dönüş değerlerini bir istemci ve hizmet arasında geçirirken, bir veri anlaşması bir temel sınıftan gönderilemez. Nesne yönelimli programlama sacayakları uygun olarak budur. Önceki örnekte, bir nesne türü `Person` ne zaman gönderilemez bir `Employee` beklenir.  
  
 Bir temel sınıftan bir veri sözleşmesi bekleniyor ancak yalnızca alan uç noktası "türetilmiş bir tür kullanarak biliyorsa" olduğunda bir veri anlaşması türetilmiş bir sınıftan gönderilebilir <xref:System.Runtime.Serialization.KnownTypeAttribute>. Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Önceki örnekte, bir nesne türü `Employee` ne zaman gönderilebilecek bir `Person` beklenen, ancak alıcı kodu içeriyorsa yalnızca <xref:System.Runtime.Serialization.KnownTypeAttribute> bilinen türler listesine eklemek için.  
  
 Parametreler ve dönüş değerleri beklenen tür bir arabirimse uygulamalar arasında geçirirken, beklenen tür türünde olan eşdeğer <xref:System.Object>. Her tür sonuçta öğesinden türetildiği için <xref:System.Object>, her veri anlaşması için veri anlaşması sonuç olarak türetilen <xref:System.Object>. Bu nedenle, herhangi bir veri anlaşması türü bir arabirim beklendiğinde geçirilebilir. Başarıyla arabirimleri ile çalışmak için ek adımlar gereklidir; Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Üye Sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Veri Sözleşmesi Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Veri Sözleşmesi Adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
