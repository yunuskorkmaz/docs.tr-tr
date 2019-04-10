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
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="653c6-102">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="653c6-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="653c6-103">Bu konu, temel bir sınıf veya yapıda kullanarak bir veri sözleşmesi oluşturma adımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="653c6-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="653c6-104">Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="653c6-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="653c6-105">Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında size kılavuzluk eder bir öğretici için bkz [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="653c6-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="653c6-106">Bir temel hizmet ve istemci oluşan bir çalışan örnek uygulama için bkz. [temel veri anlaşması](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="653c6-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="653c6-107">Bir sınıf veya yapı için temel bir veri sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="653c6-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="653c6-108">Uygulayarak türü veri anlaşması olduğunu bildirmek <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı.</span><span class="sxs-lookup"><span data-stu-id="653c6-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="653c6-109">Öznitelikler olmadan dahil olmak üzere tüm ortak türlerin seri hale getirilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="653c6-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="653c6-110"><xref:System.Runtime.Serialization.DataContractSerializer> , Bir veri anlaşması çıkarsar <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği eksik.</span><span class="sxs-lookup"><span data-stu-id="653c6-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="653c6-111">Daha fazla bilgi için [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="653c6-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="653c6-112">Uygulama tarafından seri hale üyeleri (özelliklere, alanlara veya olayları) tanımlamak <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik her üyesine.</span><span class="sxs-lookup"><span data-stu-id="653c6-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="653c6-113">Bu üyeler, veri üyeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="653c6-113">These members are called data members.</span></span> <span data-ttu-id="653c6-114">Varsayılan olarak, tüm ortak türlerin seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="653c6-114">By default, all public types are serializable.</span></span> <span data-ttu-id="653c6-115">Daha fazla bilgi için [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="653c6-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="653c6-116">Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği için özel alanlar, verilerin diğerlerine gösterilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="653c6-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="653c6-117">Üye hassas veriler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="653c6-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="653c6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="653c6-118">Example</span></span>  
 <span data-ttu-id="653c6-119">Aşağıdaki örnek, bir veri anlaşması için oluşturma işlemi gösterilmektedir `Person` uygulayarak türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfını ve üyelerini için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="653c6-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="653c6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="653c6-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="653c6-121">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="653c6-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="653c6-122">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="653c6-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="653c6-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="653c6-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
