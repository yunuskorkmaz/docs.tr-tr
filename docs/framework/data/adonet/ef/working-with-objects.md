---
title: "Nesnelerle çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 338d8a55-05cc-46b0-bbb8-1379d77068e9
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 44dd517f08b4a408a0f7c70964c6bc53ca663afd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="working-with-objects"></a><span data-ttu-id="a80be-102">Nesnelerle çalışma</span><span class="sxs-lookup"><span data-stu-id="a80be-102">Working with Objects</span></span>
<span data-ttu-id="a80be-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Sorgu, ekleme, güncelleştirme ve varlık türleri örnekleri olan belirtilmiş ortak dil çalışma zamanı (CLR) nesneleri ifade edilen silme verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a80be-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to query, insert, update, and delete data, which is expressed as typed common language runtime (CLR) objects that are instances of entity types.</span></span> <span data-ttu-id="a80be-104">Varlık türleri kavramsal modelde tanımlanan varlık temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a80be-104">The entity types represent the entities defined in the conceptual model.</span></span> <span data-ttu-id="a80be-105">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Varlıkları ve bir veri kaynağına kavramsal modelde tanımlanan ilişkiler eşler.</span><span class="sxs-lookup"><span data-stu-id="a80be-105">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] maps entities and relationships that are defined in a conceptual model to a data source.</span></span> <span data-ttu-id="a80be-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Aşağıdakileri yapmak için gerekli olanakları sağlar: nesneler olarak veri kaynağından döndürülen veriler gerçekleştirmeye; nesnelerde yapılan değişiklikleri izle; eşzamanlılık işleme; geri; veri kaynağı nesnesi değişiklikleri yaymak ve nesneleri denetimlere bağlama.</span><span class="sxs-lookup"><span data-stu-id="a80be-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provides facilities to do the following: materialize data returned from the data source as objects; track changes that were made to the objects; handle concurrency; propagate object changes back to the data source; and bind objects to controls.</span></span>  
  
 <span data-ttu-id="a80be-107">Entity Framework bakın, en son sürümünü nesneleri ile çalışma hakkında daha fazla bilgi için [nesneleriyle çalışma](http://go.microsoft.com/fwlink/?LinkId=235289).</span><span class="sxs-lookup"><span data-stu-id="a80be-107">For more information about working with objects in the latest version of the Entity Framework see, [Working with Objects](http://go.microsoft.com/fwlink/?LinkId=235289).</span></span>
