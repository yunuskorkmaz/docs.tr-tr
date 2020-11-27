---
title: 'Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma'
description: DataContractAttribute özniteliğini kullanarak WCF 'de sınıf veya yapı kullanarak bir veri sözleşmesi oluşturmayı öğrenmek için bu örneği izleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 5634eb3d3ec18d95fd7d6b3c89b572ab4f5b8eca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254044"
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
- [Veri Sözleşmelerini Kullanma](using-data-contracts.md)
- [Başlangıç Öğreticisi](../getting-started-tutorial.md)
- [Başlarken](../samples/getting-started-sample.md)
