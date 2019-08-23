---
title: 'Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968456"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma
Bu konu başlığı altında, bir sınıf veya yapı kullanarak bir veri sözleşmesi oluşturmaya yönelik temel adımlar gösterilmektedir. Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında izlenecek bir öğretici için bkz. [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Temel bir hizmet ve istemciden oluşan çalışan bir örnek uygulama için bkz. [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Bir sınıf veya yapı için temel veri sözleşmesi oluşturmak için  
  
1. Sınıfına <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini uygulayarak türün bir veri sözleşmesine sahip olduğunu bildirin. Öznitelikleri olmayanlar dahil olmak üzere tüm genel türlerin serileştirilebilir olduğunu unutmayın. Özniteliğiyoksa<xref:System.Runtime.Serialization.DataContractAttribute> bir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesini anlar. Daha fazla bilgi için bkz. [serileştirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Her üyeye <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanarak serileştirilmiş olan üyeleri (özellikler, alanlar veya olaylar) tanımlayın. Bu üyelere veri üyeleri denir. Varsayılan olarak, tüm genel türler serileştirilebilir değildir. Daha fazla bilgi için bkz. [serileştirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    > <xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği özel alanlara uygulayabilir ve verilerin başkalarına gösterilmesini sağlayabilirsiniz. Üyenin gizli veriler içermediğinden emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini sınıfına ve üyelerine uygulayarak tür için bir veri sözleşmesinin nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
