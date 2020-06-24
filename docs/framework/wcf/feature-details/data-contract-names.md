---
title: Veri Sözleşmesi Adları
description: Benzer veri sözleşmeleri kullanarak iletişimi destekleyen, WCF altyapısının veri sözleşmesini ve üye adlandırma kurallarını ve varsayılan davranışını bulun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 85c533d683558520d46f259db0bdb34dcb1214c9
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247409"
---
# <a name="data-contract-names"></a>Veri Sözleşmesi Adları

Bazen bir istemci ve hizmet aynı türleri paylaşmaz. Veri sözleşmeleri her iki tarafta de eşdeğer olduğu sürece verileri birbirlerine geçirmeye devam edebilirler. [Veri sözleşmesi denklik](data-contract-equivalence.md) , veri sözleşmesi ve veri üyesi adlarını temel alır ve bu nedenle türleri ve üyeleri bu adlarla eşlemek için bir mekanizma sağlanır. Bu konu başlığı altında, ad oluştururken veri sözleşmelerini adlandırma ve Windows Communication Foundation (WCF) altyapısının varsayılan davranışını açıklayan kurallar açıklanmaktadır.

## <a name="basic-rules"></a>Temel kurallar
Adlandırma verileri sözleşmeleri ile ilgili temel kurallar şunlardır:

- Tam nitelikli bir veri anlaşması adı, bir ad alanı ve bir ad içerir.

- Veri üyeleri yalnızca adlara sahiptir, ancak ad alanı içermez.

- Veri sözleşmeleri işlenirken, WCF altyapısı hem ad alanları hem de veri sözleşmeleri ve veri üyeleri için büyük/küçük harfe duyarlıdır.

## <a name="data-contract-namespaces"></a>Veri anlaşması ad alanları
Veri sözleşmesi ad alanı Tekdüzen Kaynak tanımlayıcısı (URI) biçimini alır. URI mutlak ya da göreli olabilir. Varsayılan olarak, belirli bir türe ait veri sözleşmeleri, bu türün ortak dil çalışma zamanı (CLR) ad alanından gelen bir ad alanı atanır.

Varsayılan olarak, tüm verilen CLR ad alanı ( *clr. Namespace*biçiminde) ad alanına eşlenir `http://schemas.datacontract.org/2004/07/Clr.Namespace` . Bu varsayılanı geçersiz kılmak için, <xref:System.Runtime.Serialization.ContractNamespaceAttribute> özniteliği modülün veya derlemenin tamamına uygulayın. Alternatif olarak, her tür için veri sözleşmesi ad alanını denetlemek için, <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> özelliğini ayarlayın <xref:System.Runtime.Serialization.DataContractAttribute> .

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization`Ad alanı ayrılmıştır ve bir veri anlaşması ad alanı olarak kullanılamaz.

> [!NOTE]
> Bildirimleri içeren veri anlaşması türlerinde varsayılan ad alanını geçersiz kılamazsınız `delegate` .

## <a name="data-contract-names"></a>Veri Sözleşmesi Adları
Belirli bir tür için bir veri sözleşmesinin varsayılan adı bu türün adıdır. Varsayılanı geçersiz kılmak için <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> , öğesinin özelliğini <xref:System.Runtime.Serialization.DataContractAttribute> alternatif bir ad olarak ayarlayın. Genel türler için özel kurallar, bu konunun ilerleyen kısımlarında "genel türler için veri sözleşmesi adları" bölümünde açıklanmaktadır.

## <a name="data-member-names"></a>Veri üyesi adları
Belirli bir alan veya özellik için bir veri üyesinin varsayılan adı, bu alanın veya özelliğin adıdır. Varsayılanı geçersiz kılmak için <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> , öğesinin özelliğini <xref:System.Runtime.Serialization.DataMemberAttribute> alternatif bir değere ayarlayın.

### <a name="examples"></a>Örnekler
Aşağıdaki örnek, veri sözleşmeleri ve veri üyelerinin varsayılan adlandırma davranışını nasıl geçersiz kılabileceğiniz gösterilmektedir.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Genel türler için veri sözleşmesi adları
Genel türler için veri sözleşmesi adlarını belirlemek için özel kurallar mevcuttur. Bu kurallar, aynı genel türün iki kapalı genel türü arasında veri anlaşması ad çakışmalarını önlemeye yardımcı olur.

Varsayılan olarak, genel bir türün veri sözleşme adı, türün adı, ardından Genel parametrelerin veri sözleşmesi adları ve genel parametrelerin veri sözleşmesi ad alanları kullanılarak hesaplanan bir *karma* tarafından izlenir. Karma, bir veri parçasını benzersiz bir şekilde tanımlayan "parmak izi" olarak davranan matematik işlevinin sonucudur. Genel parametrelerin tümü ilkel türse, karma atlanır.

Örneğin, aşağıdaki örnekteki türlere bakın.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

Bu örnekte, tür " `Drawing<Square,RegularRedBrush>` DrawingOfSquareRedBrush5HWGAU6h" veri sözleşmesi adına sahiptir; burada "5HWGAU6h" "urn: Shapes" ve "urn: default" ad alanlarının bir karmasıdır. Tür " `Drawing<Square,SpecialRedBrush>` DrawingOfSquareRedBrushjpB5LgQ_S" veri anlaşması adına sahiptir; burada "jpB5LgQ_S" "urn: Shapes" ve "urn: Special" ad alanlarının bir karmasıdır. Karma kullanılmazsa, iki adın özdeş olduğunu ve bu nedenle bir ad çarpışmasının oluştuğunu unutmayın.

## <a name="customizing-data-contract-names-for-generic-types"></a>Genel türler için veri sözleşme adlarını özelleştirme

Bazen, daha önce açıklandığı gibi genel türler için oluşturulan veri sözleşmesi adları kabul edilemez. Örneğin, ad çarpışmalarının içinde çalıştırılmayacak ve karmayı kaldırmak isteyebileceğiniz hakkında daha fazla bilgi alabilirsiniz. Bu durumda, <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> ad oluşturmak için farklı bir yol belirtmek için özelliğini kullanabilirsiniz. `Name`Genel parametrelerin veri sözleşmesi adlarına başvurmak için, özelliğinin içindeki küme ayraçları içindeki sayıları kullanabilirsiniz. (0 birinci parametreye başvurur, 1 ikincisine başvurur ve bu şekilde devam eder.) Karmaya başvurmak için bir sayı (#) ile küme ayraçları arasında bir oturum kullanabilirsiniz. Bu başvuruların her birini birden çok kez kullanabilir veya hiç kullanamazsınız.

Örneğin, yukarıdaki genel `Drawing` tür aşağıdaki örnekte gösterildiği gibi bildirilmiştir.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

Bu durumda, tür `Drawing<Square,RegularRedBrush>` "Drawing_using_RedBrush_brush_and_Square_shape" veri anlaşması adına sahiptir. Özellikte bir "{#}" olduğunda <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> , karma adının bir parçası olmadığından ve bu nedenle tür, adlandırma çakışmalarına açıktır; Örneğin, tür `Drawing<Square,SpecialRedBrush>` tam olarak aynı veri anlaşması adına sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Veri Sözleşmesi Eşitliği](data-contract-equivalence.md)
- [Veri Sözleşmesi Adları](data-contract-names.md)
- [Veri Sözleşmesi Sürümü Oluşturma](data-contract-versioning.md)
