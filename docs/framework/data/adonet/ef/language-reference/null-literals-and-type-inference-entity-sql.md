---
title: Null değişmez değerler ve tür çıkarımı (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: bb2d9184e17ee2a9916a731eb20eefa105a73753
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249819"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="98db5-102">Null değişmez değerler ve tür çıkarımı (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="98db5-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="98db5-103">Null sabit değerleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür sistemindeki herhangi bir türle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="98db5-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="98db5-104">Ancak, doğru bir sabit değerin doğru bir şekilde çıkarsanmayacak şekilde, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null bir sabit değerin kullanılabileceği belirli kısıtlamaları uygular.</span><span class="sxs-lookup"><span data-stu-id="98db5-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="98db5-105">Yazılan null değerler</span><span class="sxs-lookup"><span data-stu-id="98db5-105">Typed Nulls</span></span>  
 <span data-ttu-id="98db5-106">Yazılan boş değerler her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98db5-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="98db5-107">Tür bilindiğinden tür çıkarımı türü belirtilmiş null değerler için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="98db5-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="98db5-108">Örneğin, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yapı ile Int16 türünde bir null oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98db5-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="98db5-109">Serbest kayan boş sabit değerler</span><span class="sxs-lookup"><span data-stu-id="98db5-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="98db5-110">Serbest kayan null sabit değerleri aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="98db5-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="98db5-111">ATAMA veya Işleme ifadesine bir bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="98db5-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="98db5-112">Bu, türü belirtilmiş null bir ifade oluşturmak için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="98db5-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="98db5-113">Bir yönteme veya işleve bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="98db5-113">As an argument to a method or a function.</span></span> <span data-ttu-id="98db5-114">Standart aşırı yükleme kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="98db5-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="98db5-115">Bağımsız değişkenlerden biri olarak +,-, veya/gibi bir aritmetik ifadeye.</span><span class="sxs-lookup"><span data-stu-id="98db5-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="98db5-116">Diğer bağımsız değişkenler null sabit değerler olamaz, aksi takdirde tür çıkarımı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="98db5-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="98db5-117">Bir mantıksal ifadeye bağımsız değişkenlerden biri olarak (ve, veya DEĞIL).</span><span class="sxs-lookup"><span data-stu-id="98db5-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="98db5-118">Tüm bağımsız değişkenlerin Boole türünde olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="98db5-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="98db5-119">Bağımsız değişkeni NULL veya NULL ifade DEĞIL.</span><span class="sxs-lookup"><span data-stu-id="98db5-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="98db5-120">BENZER bir ifadeye bir veya daha fazla bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="98db5-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="98db5-121">Tüm bağımsız değişkenlerin dize olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="98db5-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="98db5-122">Adlandırılmış tür oluşturucusuna bir veya daha fazla bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="98db5-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="98db5-123">Bir çok kümeli oluşturucuya bağımsız değişkenlerden biri veya birkaçı.</span><span class="sxs-lookup"><span data-stu-id="98db5-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="98db5-124">Çoklu küme oluşturucusuna en az bir bağımsız değişken null değişmez değer olmayan bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98db5-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="98db5-125">Bir CASE ifadesinde bir veya daha fazla ifade veya ELSE ifadesi olarak.</span><span class="sxs-lookup"><span data-stu-id="98db5-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="98db5-126">CASE ifadesinde en az bir tane ya da ELSE ifadesi null değişmez değer dışında bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98db5-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="98db5-127">Serbest kayan null sabit değerleri diğer senaryolarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98db5-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="98db5-128">Örneğin, bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98db5-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98db5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98db5-129">See also</span></span>

- [<span data-ttu-id="98db5-130">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98db5-130">Entity SQL Overview</span></span>](entity-sql-overview.md)
