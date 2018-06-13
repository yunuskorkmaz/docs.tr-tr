---
title: Veri Sözleşmesi Adları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 18ba9aa1f7af3733acd60924d0aa24ceb1b5126c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494276"
---
# <a name="data-contract-names"></a>Veri Sözleşmesi Adları
Bazen bir istemci ve hizmet aynı türlerini paylaşmayın. Veri sözleşmeleri iki tarafta da eşdeğer sürece bunlar hala veri birbirlerine geçirebilirsiniz. [Veri sözleşmesi eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md) veri sözleşmesi ve veri üye adları, temel alır ve bu nedenle türleri ve üyeleri bu adlarıyla eşlemek için bir mekanizma sağlanır. Bu konu, Windows Communication Foundation (WCF) Altyapısı'nın varsayılan davranışını yanı sıra veri sözleşmeleri adları oluşturulurken adlandırma kurallarını açıklar.  
  
## <a name="basic-rules"></a>Temel kurallar  
 Sözleşmeler dahil adlandırma veri ilgili temel kurallarını:  
  
-   Tam veri sözleşme adına, bir ad ve bir ad oluşur.  
  
-   Veri üyeleri yalnızca adlarını, ancak ad alanı vardır.  
  
-   Veri sözleşmeleri işlerken WCF altyapı hem ad hem de veri sözleşmeleri ve veri üyeleri adları küçük harf duyarlıdır.  
  
## <a name="data-contract-namespaces"></a>Veri sözleşmesi ad alanları  
 Veri sözleşmesi ad formun Tekdüzen Kaynak Tanımlayıcısı (URI) alır. URI mutlak veya göreli olabilir. Varsayılan olarak, belirli bir tür için veri sözleşmeleri ortak dil çalışma zamanı (CLR) ad Türü alanından gelen bir ad alanı atanır.  
  
 Varsayılan olarak, tüm belirtilen CLR ad alanı (biçimde *Clr.Namespace*) ad alanına eşlenir "http://schemas.datacontract.org/2004/07/Clr.Namespace". Bu varsayılanı geçersiz kılmak için uygulama <xref:System.Runtime.Serialization.ContractNamespaceAttribute> tüm modüle ya da derleme özniteliği. Alternatif olarak, her tür için veri sözleşmesi ad denetlemek için ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
> [!NOTE]
>  "http://schemas.microsoft.com/2003/10/Serialization"Ad alanı ayrılmıştır ve bir veri sözleşmesi ad kullanılamaz.  
  
> [!NOTE]
>  Varsayılan ad alanını içeren veri sözleşme türleri geçersiz kılamaz `delegate` bildirimleri.  
  
## <a name="data-contract-names"></a>Veri Sözleşmesi Adları  
 Belirli bir türde bir veri sözleşmesi varsayılan adını türü adıdır. Varsayılan yerine geçecek şekilde ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute> için bir diğer ad. Genel türler için özel kurallar "Veri sözleşmesi adları için genel türleri" Bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
## <a name="data-member-names"></a>Veri üye adları  
 Verilen alan veya özellik için bir veri üyesi varsayılan adını, alan veya özellik adıdır. Varsayılan yerine geçecek şekilde ayarlanmış <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> alternatif bir değer.  
  
### <a name="examples"></a>Örnekler  
 Aşağıdaki örnek veri sözleşmeleri ve veri üyeleri davranışını adlandırma varsayılan ayarlarını geçersiz kılabilir nasıl gösterir.  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>Genel türler için veri sözleşmesi adları  
 Genel türler için veri sözleşmesi adları belirlemek için özel kurallar mevcut. Bu kurallar, aynı genel türde iki kapalı genel türler arasında veri sözleşmesi ad çakışmaları korunmanıza yardımcı olun.  
  
 Varsayılan olarak, veri sözleşme adı için genel bir tür "," dizesi tarafından izlenen türünün adı ve ardından genel parametreler veri sözleşmesi adları ve ardından bir *karma* veri sözleşmesi ad alanlarını kullanılarak hesaplanır Genel parametreler. "Veri parçası olarak tanıtan bir parmak izi" davranır matematiksel bir işlevin sonucu karmasıdır. Genel Parametreler ilkel türler tümü, karma atlanır.  
  
 Örneğin, aşağıdaki örnekte türleri bölümüne bakın.  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 Bu örnekte, türü `Drawing<Square,RegularRedBrush>` veri sözleşme adına "DrawingOfSquareRedBrush5HWGAU6h", "5HWGAU6h", "urn: şekiller" ve "urn: varsayılan" ad karmasını olduğu sahiptir. Türü `Drawing<Square,SpecialRedBrush>` veri sözleşme adına "DrawingOfSquareRedBrushjpB5LgQ_S", "jpB5LgQ_S", "urn: şekiller" ve "urn: özel" ad alanları karmasını olduğu sahiptir. Karma kullanılmazsa, iki ad aynıdır ve bu nedenle bir ad çakışması ortaya çıkar unutmayın.  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>Genel türler için özelleştirme veri sözleşmesi adları  
 Bazı durumlarda, daha önce açıklandığı gibi genel türleri için oluşturulan veri sözleşmesi adları kabul edilemez. Örneğin, ad çakışmaları çalışmaz ve karma kaldırmak isteyebilirsiniz önceden biliyorsunuz. Bu durumda, kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği `DataContractAttribute` öznitelik adları oluşturmak için farklı bir yol belirtin. Süslü ayraçlar içinde numaralarını kullanabileceğiniz `Name` veri sözleşmesi adları genel parametrelerinin başvurmak için özellik. (0 ilk parametresine başvuruyor, ikinci ve benzeri için 1 gösterir.) Karma başvurmak için bir sayı (#) işareti süslü ayraçlar içinde kullanabilirsiniz. Her bu başvuruları birden çok kez veya hiç kullanabilirsiniz.  
  
 Örneğin, genel önceki `Drawing` türü bildirilmiş aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 Bu durumda, türü `Drawing<Square,RegularRedBrush>` "Drawing_using_RedBrush_brush_and_Square_shape" veri sözleşme adına sahip. Olduğundan unutmayın bir "{#}" içinde <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği, karma adının bir kısmını değil ve bu nedenle türü adlandırma için açıktır çakışmaları; Örneğin, türü `Drawing<Square,SpecialRedBrush>` tam olarak aynı veri sözleşme adına sahip.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Veri Anlaşması Adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Veri Anlaşması Sürümü Oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
