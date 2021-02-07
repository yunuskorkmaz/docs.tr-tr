---
description: 'Hakkında daha fazla bilgi edinin: User-Defined Işlevleri'
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: d27abd78e15ad6cb5ce4e9440ac425159a0b5bdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680947"
---
# <a name="user-defined-functions"></a><span data-ttu-id="48563-103">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="48563-103">User-Defined Functions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48563-104">Kullanıcı tanımlı işlevleri göstermek için nesne modelinizdeki yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="48563-104">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="48563-105">Özniteliği ve gereken yerlerde özniteliği uygulayarak yöntemleri işlev olarak belirlersiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="48563-105">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="48563-106">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="48563-106">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="48563-107"><xref:System.InvalidOperationException>' I önlemek için, içindeki kullanıcı tanımlı işlevlerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="48563-107">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="48563-108">Doğru eşleme özniteliklerine sahip bir yöntem çağrısı olarak Sarmalanan bir işlev.</span><span class="sxs-lookup"><span data-stu-id="48563-108">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="48563-109">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="48563-109">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="48563-110">Öğesine özgü statik bir SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48563-110">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="48563-111">.NET Framework yöntemi tarafından desteklenen bir işlev.</span><span class="sxs-lookup"><span data-stu-id="48563-111">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="48563-112">Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48563-112">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="48563-113">Visual Studio kullanan geliştiriciler genellikle Kullanıcı tanımlı işlevleri eşlemek için Nesne İlişkisel Tasarımcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="48563-113">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48563-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="48563-114">In This Section</span></span>  

 [<span data-ttu-id="48563-115">Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="48563-115">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="48563-116">Skaler değerler döndüren bir işlevin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="48563-116">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="48563-117">Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="48563-117">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="48563-118">Tablo değerlerini döndüren bir işlevin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="48563-118">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="48563-119">Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="48563-119">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="48563-120">İşlev için satır içi çağrıların ve çağrının satır içi yapıldığında yürütme farklılıklarının nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="48563-120">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
