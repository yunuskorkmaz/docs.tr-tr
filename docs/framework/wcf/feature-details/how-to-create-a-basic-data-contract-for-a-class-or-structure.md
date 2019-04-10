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
ms.openlocfilehash: 4e5e6b77cdb13c17557f176a37fbb9e7d42ab667
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346008"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma
Bu konu, temel bir sınıf veya yapıda kullanarak bir veri sözleşmesi oluşturma adımlarını gösterir. Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında size kılavuzluk eder bir öğretici için bkz [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Bir temel hizmet ve istemci oluşan bir çalışan örnek uygulama için bkz. [temel veri anlaşması](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Bir sınıf veya yapı için temel bir veri sözleşmesi oluşturma  
  
1. Uygulayarak türü veri anlaşması olduğunu bildirmek <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı. Öznitelikler olmadan dahil olmak üzere tüm ortak türlerin seri hale getirilebilir olduğunu unutmayın. <xref:System.Runtime.Serialization.DataContractSerializer> , Bir veri anlaşması çıkarsar <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği eksik. Daha fazla bilgi için [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Uygulama tarafından seri hale üyeleri (özelliklere, alanlara veya olayları) tanımlamak <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik her üyesine. Bu üyeler, veri üyeleri olarak adlandırılır. Varsayılan olarak, tüm ortak türlerin seri hale getirilebilir. Daha fazla bilgi için [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği için özel alanlar, verilerin diğerlerine gösterilmesine neden olur. Üye hassas veriler içermediğinden emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir veri anlaşması için oluşturma işlemi gösterilmektedir `Person` uygulayarak türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfını ve üyelerini için öznitelikler.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
