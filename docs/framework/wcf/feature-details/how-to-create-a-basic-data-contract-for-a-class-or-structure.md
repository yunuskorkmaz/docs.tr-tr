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
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="f46e7-102">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f46e7-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="f46e7-103">Bu konu başlığı altında, bir sınıf veya yapı kullanarak bir veri sözleşmesi oluşturmaya yönelik temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f46e7-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="f46e7-104">Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f46e7-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="f46e7-105">Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında izlenecek bir öğretici için bkz. [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f46e7-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="f46e7-106">Temel bir hizmet ve istemciden oluşan çalışan bir örnek uygulama için bkz. [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f46e7-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="f46e7-107">Bir sınıf veya yapı için temel veri sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f46e7-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="f46e7-108">Sınıfına <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini uygulayarak türün bir veri sözleşmesine sahip olduğunu bildirin.</span><span class="sxs-lookup"><span data-stu-id="f46e7-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="f46e7-109">Öznitelikleri olmayanlar dahil olmak üzere tüm genel türlerin serileştirilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f46e7-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="f46e7-110">Özniteliğiyoksa<xref:System.Runtime.Serialization.DataContractAttribute> bir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesini anlar.</span><span class="sxs-lookup"><span data-stu-id="f46e7-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="f46e7-111">Daha fazla bilgi için bkz. [serileştirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="f46e7-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="f46e7-112">Her üyeye <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanarak serileştirilmiş olan üyeleri (özellikler, alanlar veya olaylar) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f46e7-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="f46e7-113">Bu üyelere veri üyeleri denir.</span><span class="sxs-lookup"><span data-stu-id="f46e7-113">These members are called data members.</span></span> <span data-ttu-id="f46e7-114">Varsayılan olarak, tüm genel türler serileştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="f46e7-114">By default, all public types are serializable.</span></span> <span data-ttu-id="f46e7-115">Daha fazla bilgi için bkz. [serileştirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="f46e7-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f46e7-116"><xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği özel alanlara uygulayabilir ve verilerin başkalarına gösterilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46e7-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="f46e7-117">Üyenin gizli veriler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f46e7-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f46e7-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f46e7-118">Example</span></span>  
 <span data-ttu-id="f46e7-119">Aşağıdaki örnek, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini sınıfına ve üyelerine uygulayarak tür için bir veri sözleşmesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f46e7-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f46e7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f46e7-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="f46e7-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f46e7-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="f46e7-122">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="f46e7-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="f46e7-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f46e7-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
