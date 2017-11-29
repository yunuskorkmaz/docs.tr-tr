---
title: "Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c5f82e2445e816c4e577e6ce5b0c8c4e2359221
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="35286-102">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="35286-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="35286-103">Bu konu, temel sınıf veya yapı kullanarak bir veri sözleşmesi oluşturma adımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35286-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="35286-104">Veri sözleşmeleri ve kullanıldıkları bkz [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="35286-104"> data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="35286-105">Temel bir oluşturma adımları bir öğretici için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="35286-105">For a tutorial that walks through the steps of creating a basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="35286-106">Bir temel hizmet ve istemci oluşan çalışan bir örnek uygulama için bkz: [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="35286-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="35286-107">Bir sınıf veya yapı için temel bir veri sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="35286-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="35286-108">Uygulayarak türü bir veri sözleşmesi olduğunu bildirmek <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı.</span><span class="sxs-lookup"><span data-stu-id="35286-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="35286-109">Öznitelikler, olmayanlar da dahil olmak üzere tüm genel türleri seri hale getirilebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="35286-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="35286-110"><xref:System.Runtime.Serialization.DataContractSerializer> , Bir veri sözleşmesi oluşturur <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="35286-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="35286-111">[Seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="35286-111"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="35286-112">Uygulayarak serileştirilmiş üyeleri (özellikleri, alanlar veya olayları) tanımlamak <xref:System.Runtime.Serialization.DataMemberAttribute> her üyesine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="35286-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="35286-113">Veri üyeleri bu üyeler denir.</span><span class="sxs-lookup"><span data-stu-id="35286-113">These members are called data members.</span></span> <span data-ttu-id="35286-114">Varsayılan olarak, tüm genel türleri seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="35286-114">By default, all public types are serializable.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="35286-115">[Seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="35286-115"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35286-116">Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği özel alanlara başkalarına gösterilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35286-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="35286-117">Üye hassas verileri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="35286-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35286-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="35286-118">Example</span></span>  
 <span data-ttu-id="35286-119">Aşağıdaki örnek bir veri sözleşmesi için oluşturulacağını gösterir `Person` uygulayarak türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı ve üyelerini öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="35286-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="35286-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35286-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="35286-121">Veri sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="35286-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="35286-122">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="35286-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="35286-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="35286-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
