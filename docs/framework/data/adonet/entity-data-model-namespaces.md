---
title: "Varlık veri modeli: ad alanları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e473453576f04e89b58806c5140e29855d7d022
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="03a17-102">Varlık veri modeli: ad alanları</span><span class="sxs-lookup"><span data-stu-id="03a17-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="03a17-103">Varlık veri modeli (EDM) ad alanı için bir Özet kapsayıcıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md), [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md), ve [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="03a17-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="03a17-104">EDM ad alanları, ad alanları bir programlama dili benzerdir: içerirler nesneler için bağlamı ve aynı ada sahip (ancak farklı ad alanlarında bulunan) nesneleri belirsizliğini ortadan kaldırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="03a17-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a17-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a17-105">Example</span></span>  
 <span data-ttu-id="03a17-106">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="03a17-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="03a17-107">Aşağıdaki CSDL kodu farklı bir kavramsal modelde tanımlanan bir türü tanımlamak için bir ad alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="03a17-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="03a17-108">Örnek, bir varlık türünü tanımlar (`Publisher`), bir karmaşık tür özelliğe sahiptir (`Address`) öğesinden alınan `ExtendedBooksModel` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="03a17-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="03a17-109">Unutmayın `Using` öğesi gösteren bir ad alanı içeri aktarıldı.</span><span class="sxs-lookup"><span data-stu-id="03a17-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="03a17-110">Ayrıca türünü `Address` özelliği, tam olarak nitelenmiş adını kullanarak tanımlanır (`ExtendedBooksModel.Address`), bu tür tanımlanan belirten `ExtendedBooksModel` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="03a17-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="03a17-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03a17-111">See Also</span></span>  
 [<span data-ttu-id="03a17-112">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="03a17-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="03a17-113">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="03a17-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
