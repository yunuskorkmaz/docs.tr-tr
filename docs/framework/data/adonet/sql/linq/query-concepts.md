---
title: "Sorgu kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a125749-ccb5-49d5-999d-d2db7171d74d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 907761184256b7cf51c7c0f20fa43ee603e0ab12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="query-concepts"></a><span data-ttu-id="867cb-102">Sorgu kavramları</span><span class="sxs-lookup"><span data-stu-id="867cb-102">Query Concepts</span></span>
<span data-ttu-id="867cb-103">Bu bölümde tasarlama için anahtar kavramlar açıklanmaktadır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="867cb-103">This section describes key concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="867cb-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="867cb-104">In This Section</span></span>  
 [<span data-ttu-id="867cb-105">LINQ to SQL Sorguları</span><span class="sxs-lookup"><span data-stu-id="867cb-105">LINQ to SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-queries.md)  
 <span data-ttu-id="867cb-106">Genel başvuruyor [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] konuları ve öğeleri için belirli açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="867cb-106">Refers to general [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] topics, and explains items specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="867cb-107">İlişkilerde Sorgulama</span><span class="sxs-lookup"><span data-stu-id="867cb-107">Querying Across Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)  
 <span data-ttu-id="867cb-108">Association'ların kullanımı açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="867cb-108">Explains how to use associations in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="867cb-109">Uzak ve Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="867cb-109">Remote vs. Local Execution</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)  
 <span data-ttu-id="867cb-110">Yürütülen sorgunuzu istediğiniz yeri belirtin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="867cb-110">Explains how to specify where you want your query executed.</span></span>  
  
 [<span data-ttu-id="867cb-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="867cb-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)  
 <span data-ttu-id="867cb-112">İlişkili nesneleri ne zaman yüklediğini belirtin açıklar.</span><span class="sxs-lookup"><span data-stu-id="867cb-112">Describes how to specify when related objects are loaded.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="867cb-113">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="867cb-113">Related Sections</span></span>  
 [<span data-ttu-id="867cb-114">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="867cb-114">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="867cb-115">Açıklayan konulara bağlantılar içerir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="867cb-115">Contains links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology.</span></span>  
  
 [<span data-ttu-id="867cb-116">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="867cb-116">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 <span data-ttu-id="867cb-117">Nesne Kimliği kavramını açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="867cb-117">Explains the concept of object identity in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="867cb-118">Giriş LINQ sorgularını (C#)</span><span class="sxs-lookup"><span data-stu-id="867cb-118">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="867cb-119">Sorgu işlemlerinde tanıtılmaktadır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="867cb-119">Provides an introduction to query operations in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
