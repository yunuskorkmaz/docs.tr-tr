---
title: "Kullanıcı Tanımlı İşlevler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff13a123bcb2c61d786f2156e600a16cdd6bb31e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions"></a><span data-ttu-id="caaba-102">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="caaba-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="caaba-103">Kullanıcı tanımlı işlevler temsil etmek için nesne modelinde yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="caaba-103"> uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="caaba-104">Uygulayarak işlevleri olarak belirttiğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerektiğinde, <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="caaba-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="caaba-105">Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="caaba-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="caaba-106">Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı işlevlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="caaba-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="caaba-107">Doğru eşleme özniteliklere sahip bir yöntem çağrısı Sarmalanan işlev.</span><span class="sxs-lookup"><span data-stu-id="caaba-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="caaba-108">Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="caaba-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="caaba-109">Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="caaba-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="caaba-110">Bir işlev tarafından desteklenen bir [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaba-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="caaba-111">Bu bölümdeki konular, form ve kodu kendiniz yazarsanız, uygulamanızda bu yöntemleri çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaba-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="caaba-112">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] genellikle kullanırsınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] kullanıcı tanımlı işlevler eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="caaba-112">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="caaba-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="caaba-113">In This Section</span></span>  
 [<span data-ttu-id="caaba-114">Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın</span><span class="sxs-lookup"><span data-stu-id="caaba-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="caaba-115">Skaler değerler döndüren bir işlev uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="caaba-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="caaba-116">Nasıl yapılır: kullanıcı tanımlı tablo değerli işlevler kullanın</span><span class="sxs-lookup"><span data-stu-id="caaba-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="caaba-117">Tablo değerleri döndüren bir işlev uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="caaba-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="caaba-118">Nasıl yapılır: çağrı kullanıcı tanımlı işlevler satır içi</span><span class="sxs-lookup"><span data-stu-id="caaba-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="caaba-119">Satır içi çağrısı yapıldığında satır içi işlevler ve yürütme farklılıkları aramalarda açıklar.</span><span class="sxs-lookup"><span data-stu-id="caaba-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
