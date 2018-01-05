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
ms.workload: dotnet
ms.openlocfilehash: 833ffbbccfb35fd51ddde5dbeb4e3de3d79923ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions"></a><span data-ttu-id="4b2fd-102">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="4b2fd-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="4b2fd-103">Kullanıcı tanımlı işlevler temsil etmek için nesne modelinde yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-103"> uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="4b2fd-104">Uygulayarak işlevleri olarak belirttiğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerektiğinde, <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="4b2fd-105">Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="4b2fd-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="4b2fd-106">Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı işlevlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4b2fd-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="4b2fd-107">Doğru eşleme özniteliklere sahip bir yöntem çağrısı Sarmalanan işlev.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="4b2fd-108">Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="4b2fd-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="4b2fd-109">Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b2fd-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="4b2fd-110">Bir işlev tarafından desteklenen bir [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="4b2fd-111">Bu bölümdeki konular, form ve kodu kendiniz yazarsanız, uygulamanızda bu yöntemleri çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="4b2fd-112">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] genellikle kullanırsınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] kullanıcı tanımlı işlevler eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-112">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b2fd-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4b2fd-113">In This Section</span></span>  
 [<span data-ttu-id="4b2fd-114">Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="4b2fd-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="4b2fd-115">Skaler değerler döndüren bir işlev uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="4b2fd-116">Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="4b2fd-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="4b2fd-117">Tablo değerleri döndüren bir işlev uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="4b2fd-118">Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="4b2fd-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="4b2fd-119">Satır içi çağrısı yapıldığında satır içi işlevler ve yürütme farklılıkları aramalarda açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b2fd-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
