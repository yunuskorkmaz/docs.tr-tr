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
ms.openlocfilehash: bb2cebabc8e51870398689ea032d27c72f0503b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490074"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="394af-102">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="394af-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="394af-103">Bu konu, temel sınıf veya yapı kullanarak bir veri sözleşmesi oluşturma adımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="394af-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="394af-104">Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="394af-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="394af-105">Bir temel Windows Communication Foundation (WCF) hizmetini ve istemci oluşturma adımları bir öğretici için bkz [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="394af-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="394af-106">Bir temel hizmet ve istemci oluşan çalışan bir örnek uygulama için bkz: [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="394af-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="394af-107">Bir sınıf veya yapı için temel bir veri sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="394af-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="394af-108">Uygulayarak türü bir veri sözleşmesi olduğunu bildirmek <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı.</span><span class="sxs-lookup"><span data-stu-id="394af-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="394af-109">Öznitelikler, olmayanlar da dahil olmak üzere tüm genel türleri seri hale getirilebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="394af-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="394af-110"><xref:System.Runtime.Serialization.DataContractSerializer> , Bir veri sözleşmesi oluşturur <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="394af-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="394af-111">Daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="394af-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="394af-112">Uygulayarak serileştirilmiş üyeleri (özellikleri, alanlar veya olayları) tanımlamak <xref:System.Runtime.Serialization.DataMemberAttribute> her üyesine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="394af-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="394af-113">Veri üyeleri bu üyeler denir.</span><span class="sxs-lookup"><span data-stu-id="394af-113">These members are called data members.</span></span> <span data-ttu-id="394af-114">Varsayılan olarak, tüm genel türleri seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="394af-114">By default, all public types are serializable.</span></span> <span data-ttu-id="394af-115">Daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="394af-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="394af-116">Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği özel alanlara başkalarına gösterilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="394af-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="394af-117">Üye hassas verileri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="394af-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="394af-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="394af-118">Example</span></span>  
 <span data-ttu-id="394af-119">Aşağıdaki örnek bir veri sözleşmesi için oluşturulacağını gösterir `Person` uygulayarak türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı ve üyelerini öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="394af-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="394af-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="394af-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="394af-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="394af-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="394af-122">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="394af-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="394af-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="394af-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
