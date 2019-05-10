---
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 57675c470383fb45e9ccf34a846144b435cf4d0d
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910676"
---
# <a name="user-defined-functions"></a><span data-ttu-id="70159-102">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="70159-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="70159-103">yöntemleri, kullanıcı tanımlı işlevleri temsil etmek için nesne modelinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="70159-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="70159-104">Uygulayarak işlevleri belirlediğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerekli olduğu durumlarda <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70159-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="70159-105">Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="70159-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="70159-106">Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı içindeki işlevler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="70159-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="70159-107">Doğru eşleme özniteliklere sahip bir yöntem çağrısının sarmalanmış işlev.</span><span class="sxs-lookup"><span data-stu-id="70159-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="70159-108">Daha fazla bilgi için [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="70159-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="70159-109">Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70159-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="70159-110">Tarafından desteklenen bir işlev bir [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yöntemi.</span><span class="sxs-lookup"><span data-stu-id="70159-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="70159-111">Bu bölümdeki konular, form ve kendinize kod yazma, uygulamanız bu yöntemleri çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="70159-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="70159-112">Visual Studio kullanan geliştiricilerin genellikle kullandığınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] kullanıcı tanımlı işlevleri eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="70159-112">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70159-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="70159-113">In This Section</span></span>  
 [<span data-ttu-id="70159-114">Nasıl yapılır: Skaler değerli kullanıcı tanımlı işlevler kullanma</span><span class="sxs-lookup"><span data-stu-id="70159-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="70159-115">Skaler değerler döndüren bir işlev uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="70159-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="70159-116">Nasıl yapılır: Tablo değerli kullanıcı tanımlı işlevler kullanma</span><span class="sxs-lookup"><span data-stu-id="70159-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="70159-117">Tablo değerleri döndüren bir işlev uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="70159-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="70159-118">Nasıl yapılır: Kullanıcı tanımlı satır içi işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="70159-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="70159-119">Satır içi çağrısı yapıldığında, İşlevler ve yürütme farklılıkları satır içi çağrı yapmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="70159-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
