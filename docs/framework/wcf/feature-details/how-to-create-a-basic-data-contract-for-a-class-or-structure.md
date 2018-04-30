---
title: 'Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43fa318d2910fcd8b1d9ce75fc02d75bb39d4079
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma
Bu konu, temel sınıf veya yapı kullanarak bir veri sözleşmesi oluşturma adımlarını gösterir. Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Temel bir oluşturma adımları bir öğretici için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Bir temel hizmet ve istemci oluşan çalışan bir örnek uygulama için bkz: [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Bir sınıf veya yapı için temel bir veri sözleşmesi oluşturmak için  
  
1.  Uygulayarak türü bir veri sözleşmesi olduğunu bildirmek <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı. Öznitelikler, olmayanlar da dahil olmak üzere tüm genel türleri seri hale getirilebilir olduğuna dikkat edin. <xref:System.Runtime.Serialization.DataContractSerializer> , Bir veri sözleşmesi oluşturur <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği yok. Daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Uygulayarak serileştirilmiş üyeleri (özellikleri, alanlar veya olayları) tanımlamak <xref:System.Runtime.Serialization.DataMemberAttribute> her üyesine özniteliği. Veri üyeleri bu üyeler denir. Varsayılan olarak, tüm genel türleri seri hale getirilebilir. Daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği özel alanlara başkalarına gösterilmesine neden olabilir. Üye hassas verileri içermediğinden emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir veri sözleşmesi için oluşturulacağını gösterir `Person` uygulayarak türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı ve üyelerini öznitelikleri.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
