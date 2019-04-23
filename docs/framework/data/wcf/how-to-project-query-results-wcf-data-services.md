---
title: 'Nasıl yapılır: Proje sorgu sonuçları (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: 4b0646c2ad45a86691b86b1dd5f112f598ee2dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974811"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Nasıl yapılır: Proje sorgu sonuçları (WCF Data Services)
Projeksiyon, yalnızca belirli özellikleri bir varlığın yanıtta döndürülen belirterek bir sorgu tarafından döndürülen veri miktarını azaltmak için bir mekanizma sağlar. Projeksiyonlar sonuçları üzerinde gerçekleştirebileceğiniz bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanarak ya da sorgu `$select` sorgu seçeneği kullanarak veya [seçin](~/docs/csharp/language-reference/keywords/select-clause.md) yan tümcesi ([seçin](~/docs/visual-basic/language-reference/queries/select-clause.md) Visual Basic'te) bir LINQ Sorgu. Daha fazla bilgi için [veri hizmetini sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir LINQ Sorgu yanı sıra Identity özelliği yalnızca adresi özgü özellikleri içeren yeni bir müşteri adresi türü içinde bu projeleri müşteriler varlıkları gösterir. Bu `CustomerAddress` sınıfı istemcide tanımlanır ve istemci kitaplığının bir varlık türü olarak tanıyabilmesi uymama nedeniyle gerçekleşir.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir LINQ söz konusu projeleri döndürülen müşterilerin varlıkları yalnızca adresi özgü özellikler ve hiçbir kimlik özelliği içeren bir yeni CustomerAddressNonEntity, sorgu türü. Bu `CustomerAddressNonEntity` sınıfı istemcide tanımlanır ve bir varlık türü olarak öznitelikli değil.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tanımlarını gösterir `CustomerAddress` ve `CustomerAddressNonEntity` önceki örneklerde kullanılan türler.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
