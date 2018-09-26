---
title: Veri Sözleşmesi Adları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: cd878452f3ec99627507334a26873a004e5b5314
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196700"
---
# <a name="data-contract-names"></a>Veri Sözleşmesi Adları

Bazen bir hizmet ve bir istemci aynı türlerini paylaşmayın. Veri sözleşmeleri her iki kenarı da eşdeğer olduğu sürece kullanıcılar hala verileri birbirine geçirebilirsiniz. [Veri sözleşmesi eşitliği](data-contract-equivalence.md) veri anlaşması ve veri üye adları, temel alır ve bu nedenle türler ve üyeler bu adlarla eşlemek için bir mekanizma yoktur. Bu konu, Windows Communication Foundation (WCF) Altyapısı'nın varsayılan davranışını yanı sıra veri sözleşmeleri adları oluştururken adlandırma kurallarını açıklar.

## <a name="basic-rules"></a>Temel kurallar
Temel kurallar sözleşmeler dahil adlandırma veri ile ilgili:

- Bir tam veri anlaşması adına bir ad alanı ve bir ad oluşur.

- Veri üyeleri yalnızca adları, ancak herhangi bir ad alanı var.

- Veri sözleşmeleri işlerken, WCF altyapısı hem ad hem de veri sözleşmeleri ve veri üyelerinin adları duyarlıdır.

## <a name="data-contract-namespaces"></a>Veri anlaşması ad alanları
Bir veri anlaşması ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) alır. URI, mutlak veya göreli olabilir. Varsayılan olarak, belirli bir tür için veri sözleşmeleri ortak dil çalışma zamanı (CLR) ad Türü alanından gelen ad alanı atanır.

Varsayılan olarak, herhangi belirli bir CLR ad alanı (biçimde *Clr.Namespace*) ad alanına eşlenen `http://schemas.datacontract.org/2004/07/Clr.Namespace`. Bu varsayılanı geçersiz kılmak için geçerli <xref:System.Runtime.Serialization.ContractNamespaceAttribute> özniteliği olan tüm modül veya bütünleştirilmiş kod. Alternatif olarak, her türü için veri anlaşması ad denetlemek için ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute>.

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization` Ad ayrılmış ve bir veri anlaşması ad kullanılamaz.

> [!NOTE]
> Varsayılan ad alanı içeren bir veri anlaşması türlerinde geçersiz kılınamaz `delegate` bildirimleri.

## <a name="data-contract-names"></a>Veri Sözleşmesi Adları
Verilen tür için bir veri anlaşması varsayılan adını, bu tür adıdır. Varsayılan geçersiz kılmak için ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute> için bir diğer ad. Genel türler için özel kurallar "Veri sözleşmesi adları için genel türleri", bu konunun ilerleyen bölümlerinde açıklanmıştır.

## <a name="data-member-names"></a>Veri üye adları
Belirtilen alan veya özellik için bir veri üyesi varsayılan adını, alan veya özellik adıdır. Varsayılan geçersiz kılmak için ayarlanmış <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> için alternatif bir değer.

### <a name="examples"></a>Örnekler
Aşağıdaki örnek, varsayılan adlandırma veri sözleşmeleri ve veri üyeleri davranışını nasıl geçersiz gösterir.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Genel türler için veri sözleşmesi adları
Özel kurallar, genel türler için veri sözleşmesi adları belirlemek için mevcut. Bu kurallar, aynı genel tür iki kapalı genel türler arasında veri anlaşması ad çakışmalarını önlemek.

Varsayılan olarak, veri anlaşması adında ardından genel parametre veri sözleşmesi adları için genel bir tür "," dize tarafından izlenen bir türün adını ardından bir *karma* veri anlaşması ad alanlarını kullanarak hesaplanan Genel parametreler. "Bir veri parçasını benzersiz olarak tanımlayan bir parmak izi" görevi gören bir matematiksel işlev sonucu karmasıdır. Genel Parametreler temel türlerin tümü, karma atlanır.

Örneğin, aşağıdaki örnekte türleri bakın.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

Bu örnekte, türü `Drawing<Square,RegularRedBrush>` "5HWGAU6h", "urn: şekiller" ve "urn: varsayılan" ad alanları karması olduğu "DrawingOfSquareRedBrush5HWGAU6h" veri anlaşması adına sahip. Türü `Drawing<Square,SpecialRedBrush>` "jpB5LgQ_S", "urn: şekiller" ve "urn: özel" ad alanları karması olduğu "DrawingOfSquareRedBrushjpB5LgQ_S" veri anlaşması adına sahip. Karma kullanılmıyorsa, iki adlarının aynı olduğunu ve bu nedenle bir ad çakışması gerçekleşir. unutmayın.

## <a name="customizing-data-contract-names-for-generic-types"></a>Genel türler için özelleştirme veri sözleşmesi adları

Bazı durumlarda, daha önce açıklandığı gibi genel türler için oluşturulan veri sözleşmesi adları kabul edilemez. Örneğin, önceden ad çakışması çalışmaz ve karma kaldırmak isteyebilirsiniz haberdar olabilirsiniz. Bu durumda, kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği `DataContractAttribute` adları oluşturmak için farklı bir yol belirtmek için özniteliği. Küme ayraçları içine numaralarını kullanabileceğiniz `Name` veri sözleşmesi adları genel parametre başvurmak için özellik. (0 ilk parametresine başvuruyor, 1 saniye ve benzeri için ifade eder.) Sayı (#) işareti küme ayraçlarının içindeki karma başvurmak için kullanabilirsiniz. Her bu başvuruları birden çok kez veya hiç kullanabilirsiniz.

Örneğin, genel önceki `Drawing` türü bildirilmiş aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

Bu durumda, türü `Drawing<Square,RegularRedBrush>` "Drawing_using_RedBrush_brush_and_Square_shape" veri anlaşması adına sahip. Olduğundan unutmayın bir "{#}" içinde <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği, karma adının bir parçası değil ve bu nedenle türü için adlandırma maruz çakışmaları; Örneğin, türü `Drawing<Square,SpecialRedBrush>` tam olarak aynı veri anlaşması adına sahip.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Veri Anlaşması Eşitliği](data-contract-equivalence.md)
- [Veri Anlaşması Adları](data-contract-names.md)
- [Veri Anlaşması Sürümü Oluşturma](data-contract-versioning.md)