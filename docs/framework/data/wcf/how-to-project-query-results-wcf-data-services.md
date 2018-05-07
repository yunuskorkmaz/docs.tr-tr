---
title: 'Nasıl yapılır: Proje sorgu sonuçları (WCF Veri Hizmetleri)'
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
ms.openlocfilehash: 4b75eb21cab7cd3acf25f7bcb9a3f009e8d5748b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Nasıl yapılır: Proje sorgu sonuçları (WCF Veri Hizmetleri)
Projeksiyon yalnızca belirli özellikleri bir varlığın yanıtta döndürülen belirterek bir sorgu tarafından döndürülen veri miktarını azaltmak için bir mekanizma sağlar. Sonuçlarına tahminleri gerçekleştirebilirsiniz bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanarak sorgu `$select` sorgu seçeneğini kullanarak veya [seçin](~/docs/csharp/language-reference/keywords/select-clause.md) yan tümcesi ([seçin](~/docs/visual-basic/language-reference/queries/select-clause.md) Visual Basic'te) LINQ Sorgu. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek LINQ sorgusu yalnızca adresine özgü özellikleri artı kimlik özelliği içeren yeni bir müşteri adresi türü, o projeleri müşteriler varlıklar gösterir. Bu `CustomerAddress` sınıfı istemcide tanımlanır ve istemci kitaplığı varlık türü olarak tanıyabilmesi öznitelikli.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir LINQ yalnızca adres özgü özellikler ve hiçbir kimlik özelliği içeren yeni bir CustomerAddressNonEntity türü, o projeleri döndürülen müşteriler varlıkları sorgu. Bu `CustomerAddressNonEntity` sınıfı istemcide tanımlanır ve varlık türü olarak öznitelikli değil.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tanımlarını gösterir `CustomerAddress``CustomerAddressNonEntity` önceki örneklerde kullanılan türleri.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
