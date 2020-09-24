---
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 061e07ba91a1742c90a594bf42f12e64172b2481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164122"
---
# <a name="user-defined-functions"></a><span data-ttu-id="a0e6f-102">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="a0e6f-102">User-Defined Functions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a0e6f-103">Kullanıcı tanımlı işlevleri göstermek için nesne modelinizdeki yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="a0e6f-104">Özniteliği ve gereken yerlerde özniteliği uygulayarak yöntemleri işlev olarak belirlersiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a0e6f-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="a0e6f-105">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="a0e6f-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="a0e6f-106"><xref:System.InvalidOperationException>' I önlemek için, içindeki kullanıcı tanımlı işlevlerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="a0e6f-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="a0e6f-107">Doğru eşleme özniteliklerine sahip bir yöntem çağrısı olarak Sarmalanan bir işlev.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="a0e6f-108">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="a0e6f-108">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="a0e6f-109">Öğesine özgü statik bir SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a0e6f-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="a0e6f-110">.NET Framework yöntemi tarafından desteklenen bir işlev.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="a0e6f-111">Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="a0e6f-112">Visual Studio kullanan geliştiriciler genellikle Kullanıcı tanımlı işlevleri eşlemek için Nesne İlişkisel Tasarımcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0e6f-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a0e6f-113">In This Section</span></span>  

 [<span data-ttu-id="a0e6f-114">Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0e6f-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="a0e6f-115">Skaler değerler döndüren bir işlevin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="a0e6f-116">Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0e6f-116">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="a0e6f-117">Tablo değerlerini döndüren bir işlevin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="a0e6f-118">Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="a0e6f-118">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="a0e6f-119">İşlev için satır içi çağrıların ve çağrının satır içi yapıldığında yürütme farklılıklarının nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
