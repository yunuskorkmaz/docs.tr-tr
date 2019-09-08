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
ms.openlocfilehash: 758bb01764fcfe195d4f940705316e7579be95ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780013"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Nasıl yapılır: Proje sorgu sonuçları (WCF Veri Hizmetleri)
Projeksiyon, bir varlığın yalnızca belirli özelliklerinin yanıt olarak döndürüldüğünü belirterek, bir sorgu tarafından döndürülen veri miktarını azaltmak için bir mekanizma sağlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Sorgu seçeneğini `$select` kullanarak ya da bir LINQ sorgusunda [Select](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesini (Visual Basic içinde[seçin](../../../visual-basic/language-reference/queries/select-clause.md) ) kullanarak bir sorgunun sonuçlarında projeksiyonlar yapabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşterilerin varlıklarını, yalnızca adrese özgü özellikler ve kimlik özelliği içeren yeni bir CustomerAddress türüne uygulayan bir LINQ sorgusu gösterir. Bu `CustomerAddress` sınıf, istemci üzerinde tanımlanmıştır ve istemci kitaplığının onu bir varlık türü olarak tanıyabilmesi için öznitelikli.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşterilerin varlıklarını yalnızca adrese özgü özellikler ve hiçbir Identity özelliği içeren yeni bir CustomerAddressNonEntity türüne döndürdüğü bir LINQ sorgusunu gösterir. Bu `CustomerAddressNonEntity` sınıf, istemcide tanımlanır ve bir varlık türü olarak kullanılamaz.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, önceki örneklerde kullanılan `CustomerAddress` ve `CustomerAddressNonEntity` türlerinin tanımları gösterilmektedir.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
