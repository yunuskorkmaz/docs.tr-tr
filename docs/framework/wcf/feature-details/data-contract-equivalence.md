---
title: "Veri Sözleşmesi Eşitliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e3494c877db156ecc818c760bd0712f5e59ca0a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-contract-equivalence"></a>Veri Sözleşmesi Eşitliği
Bir hizmeti veya başarılı bir şekilde bir istemciye veri göndermek için bir hizmeti belirli bir türde veri başarıyla göndermek bir istemci için gönderilen türü mutlaka alan tarafta mevcut gerekmez. Veri sözleşmeleri her iki türdeki eşdeğer tek gereksinimdir. (Bazı durumlarda, katı eşdeğer anlatıldığı gibi gerekli değil [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Veri sözleşmeleri eşdeğer olarak aynı ad alanına ve ada sahip oldukları gerekir. Ayrıca, her veri üyesi bir tarafında diğer tarafta bir eşdeğer veri üyesi olması gerekir.  
  
 Veri üyeleri eşdeğer olarak aynı ada sahip oldukları gerekir. Ayrıca, aynı veri türünü temsil etmelidir; diğer bir deyişle, kendi veri sözleşmeleri eşdeğer olmalıdır.  
  
> [!NOTE]
>  Verileri veri üye adları, yanı sıra adları ve ad alanları sözleşme Not büyük küçük harfe duyarlıdır.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]veri sözleşmesi adları ve ad alanları yanı sıra, bkz: veri üye adı [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 İki tür mevcutsa aynı tarafında (gönderen veya alıcı) ve kendi veri sözleşmeleri eşdeğer değildir (örneğin, farklı veri üyelerinin sahip oldukları), siz bunları aynı ad ve ad vermemelisiniz. Bunun yapılması, özel durum oluşturulmasına neden olabilir.  
  
 Veri sözleşmeleri aşağıdaki türleri için eşdeğerdir:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Veri üye sırası ve veri sözleşmesi eşdeğer  
 Kullanarak <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı, veri sözleşmesi eşitliği etkileyebilir. Veri sözleşmeleri eşdeğer olarak aynı sırada görünür üyeleri olmalıdır. Varsayılan olarak alfabetik sırasıdır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Örneğin, aşağıdaki kodu eşdeğeri veri sözleşmelerinde sonuçlanır.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ancak, aşağıdakiler bir eşdeğer veri sözleşmesi oluşmaz.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Devralma, arabirimler ve veri sözleşmesi eşitliği  
 Tüm temel türü veri üyelerini içeren tek bir veri sözleşmesi ise gibi eşdeğer belirlerken, başka bir veri sözleşmesi devralan bir veri sözleşmesi kabul edilir. Veri üyeleri sırasını eşleşmelidir göz önünde bulundurun ve türetilen tür üyeleri sırada temel tür üyeleri koyun. Aşağıdaki kod örneğinde olduğu gibi iki veri üyeleri aynı sıra değeri, ayrıca, bu veri üyeleri için sıralama alfabetik varsa. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, veri türü için sözleşme `Employee` türü için veri sözleşmesi eşdeğerdir `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Türetilmiş bir sınıf bir veri sözleşmesi alıcı uç nokta bekler, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, bir veri sözleşmesi temel sınıfından gönderilemiyor. Nesne odaklı programlama tenets uygun olarak budur. Önceki örnekte, bir nesne türü `Person` ne zaman gönderilemez bir `Employee` beklenir.  
  
 Beklenen, ancak alıcı endpoint "türetilmiş bir tür kullanarak biliyorsa" tek bir veri sözleşmesi temel sınıfından türetilmiş bir sınıf bir veri sözleşmesi gönderilebilir <xref:System.Runtime.Serialization.KnownTypeAttribute>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Önceki örnekte, bir nesne türü `Employee` ne zaman gönderilebilecek bir `Person` bekleniyor ancak alıcı kodu içeriyorsa yalnızca <xref:System.Runtime.Serialization.KnownTypeAttribute> bilinen türleri listesinde dahil etmek için.  
  
 Parametreler ve dönüş değerleri beklenen tür bir arabirim ise uygulamalar arasında geçirirken, beklenen tür olan türü eşdeğer <xref:System.Object>. Türeyen sonuçta her tür için <xref:System.Object>, her veri sözleşmesi için veri sözleşmesi sonuçta türeyen <xref:System.Object>. Bu nedenle, bir arabirim beklendiğinde herhangi bir veri sözleşmesi türü geçirilebilir. Başarıyla arabirimleri ile çalışmak için ek adımlar gereklidir; Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
