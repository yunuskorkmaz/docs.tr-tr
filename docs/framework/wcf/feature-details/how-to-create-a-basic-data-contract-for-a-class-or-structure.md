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
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="48a09-103">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a09-103">How to: Create a Basic Data Contract for a Class or Structure</span></span>

<span data-ttu-id="48a09-104">Bu konu başlığı altında, bir sınıf veya yapı kullanarak bir veri sözleşmesi oluşturmaya yönelik temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48a09-104">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="48a09-105">Veri sözleşmeleri ve bunların nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="48a09-105">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="48a09-106">Temel Windows Communication Foundation (WCF) hizmet ve istemci oluşturma adımlarında izlenecek bir öğretici için bkz. [Başlangıç Öğreticisi](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="48a09-106">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="48a09-107">Temel bir hizmet ve istemciden oluşan çalışan bir örnek uygulama için bkz. [temel veri sözleşmesi](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="48a09-107">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="48a09-108">Bir sınıf veya yapı için temel veri sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="48a09-108">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="48a09-109">Sınıfına özniteliğini uygulayarak türün bir veri sözleşmesine sahip olduğunu bildirin <xref:System.Runtime.Serialization.DataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="48a09-109">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="48a09-110">Öznitelikleri olmayanlar dahil olmak üzere tüm genel türlerin serileştirilebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48a09-110">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="48a09-111"><xref:System.Runtime.Serialization.DataContractSerializer>Özniteliği yoksa bir veri sözleşmesini anlar <xref:System.Runtime.Serialization.DataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="48a09-111">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="48a09-112">Daha fazla bilgi için bkz. [serileştirilebilir türler](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="48a09-112">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="48a09-113">Her üyeye özniteliği uygulanarak serileştirilmiş olan üyeleri (özellikler, alanlar veya olaylar) tanımlayın <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="48a09-113">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="48a09-114">Bu üyelere veri üyeleri denir.</span><span class="sxs-lookup"><span data-stu-id="48a09-114">These members are called data members.</span></span> <span data-ttu-id="48a09-115">Varsayılan olarak, tüm genel türler serileştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="48a09-115">By default, all public types are serializable.</span></span> <span data-ttu-id="48a09-116">Daha fazla bilgi için bkz. [serileştirilebilir türler](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="48a09-116">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="48a09-117"><xref:System.Runtime.Serialization.DataMemberAttribute>Özniteliği özel alanlara uygulayabilir ve verilerin başkalarına gösterilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a09-117">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="48a09-118">Üyenin gizli veriler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="48a09-118">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48a09-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="48a09-119">Example</span></span>  

 <span data-ttu-id="48a09-120">Aşağıdaki örnek, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini sınıfına ve üyelerine uygulayarak tür için bir veri sözleşmesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48a09-120">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="48a09-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48a09-121">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="48a09-122">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="48a09-122">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="48a09-123">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="48a09-123">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="48a09-124">Başlarken</span><span class="sxs-lookup"><span data-stu-id="48a09-124">Getting Started</span></span>](../samples/getting-started-sample.md)
