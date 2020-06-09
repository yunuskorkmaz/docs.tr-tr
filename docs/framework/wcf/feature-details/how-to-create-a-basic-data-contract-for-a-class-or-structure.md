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
ms.openlocfilehash: 0fd7bbea4d6e8d315566aa798ed89a0fd2657f58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599041"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma
Bu konu başlığı altında, bir sınıf veya yapı kullanarak bir veri sözleşmesi oluşturmaya yönelik temel adımlar gösterilmektedir. Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).  
  
 Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında izlenecek bir öğretici için bkz. [Başlangıç Öğreticisi](../getting-started-tutorial.md). Temel bir hizmet ve istemciden oluşan çalışan bir örnek uygulama için bkz. [temel veri sözleşmesi](../samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Bir sınıf veya yapı için temel veri sözleşmesi oluşturmak için  
  
1. Sınıfına özniteliğini uygulayarak türün bir veri sözleşmesine sahip olduğunu bildirin <xref:System.Runtime.Serialization.DataContractAttribute> . Öznitelikleri olmayanlar dahil olmak üzere tüm genel türlerin serileştirilebilir olduğunu unutmayın. <xref:System.Runtime.Serialization.DataContractSerializer>Özniteliği yoksa bir veri sözleşmesini anlar <xref:System.Runtime.Serialization.DataContractAttribute> . Daha fazla bilgi için bkz. [serileştirilebilir türler](serializable-types.md).  
  
2. Her üyeye özniteliği uygulanarak serileştirilmiş olan üyeleri (özellikler, alanlar veya olaylar) tanımlayın <xref:System.Runtime.Serialization.DataMemberAttribute> . Bu üyelere veri üyeleri denir. Varsayılan olarak, tüm genel türler serileştirilebilir değildir. Daha fazla bilgi için bkz. [serileştirilebilir türler](serializable-types.md).  
  
    > [!NOTE]
    > <xref:System.Runtime.Serialization.DataMemberAttribute>Özniteliği özel alanlara uygulayabilir ve verilerin başkalarına gösterilmesini sağlayabilirsiniz. Üyenin gizli veriler içermediğinden emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini sınıfına ve üyelerine uygulayarak tür için bir veri sözleşmesinin nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Başlangıç Öğreticisi](../getting-started-tutorial.md)
- [Başlarken](../samples/getting-started-sample.md)
