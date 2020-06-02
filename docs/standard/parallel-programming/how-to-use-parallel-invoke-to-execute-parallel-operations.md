---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için parallel_invoke Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 2b353fb8cb5e04ee4cab6b49f55539ecb40fab4f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290804"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="35835-102">Nasıl yapılır: Paralel İşlemleri Yürütmek için parallel_invoke Kullanma</span><span class="sxs-lookup"><span data-stu-id="35835-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="35835-103">Bu örnek <xref:System.Threading.Tasks.Parallel.Invoke%2A> , görev paralel kitaplığı 'nda kullanarak nasıl paralel hale getirmek işlem yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35835-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="35835-104">Paylaşılan bir veri kaynağında üç işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="35835-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="35835-105">İşlemler, kaynağı değiştirmediği için doğrudan paralel şekilde yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="35835-105">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="35835-106">TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35835-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="35835-107">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="35835-107">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="35835-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="35835-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="35835-109">İle <xref:System.Threading.Tasks.Parallel.Invoke%2A> , aynı anda hangi eylemleri çalıştırmak istediğinizi ifade edersiniz ve çalışma zamanı, ana bilgisayardaki çekirdek sayısına otomatik olarak ölçekleme de dahil olmak üzere tüm iş parçacığı zamanlama ayrıntılarını işler.</span><span class="sxs-lookup"><span data-stu-id="35835-109">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="35835-110">Bu örnek, verileri değil, işlemleri paralelleştirin.</span><span class="sxs-lookup"><span data-stu-id="35835-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="35835-111">Alternatif bir yaklaşım olarak, PLıNQ kullanarak LINQ sorgularını paralel hale getirmek yapabilir ve sorguları sırayla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35835-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="35835-112">Alternatif olarak, PLıNQ kullanarak verileri paralel hale getirmek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35835-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="35835-113">Diğer bir seçenek de sorguları ve görevleri paralel hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="35835-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="35835-114">Elde edilen ek yükün görece az işlemcili konak bilgisayarlarda performansı düşürebilse de, çok işlemcili bilgisayarlarda daha iyi ölçeklendirme yapar.</span><span class="sxs-lookup"><span data-stu-id="35835-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="35835-115">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="35835-115">Compile the Code</span></span>

<span data-ttu-id="35835-116">Tüm örneği kopyalayıp bir Microsoft Visual Studio projesine yapıştırın ve **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="35835-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="35835-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35835-117">See also</span></span>

- [<span data-ttu-id="35835-118">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="35835-118">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="35835-119">Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme</span><span class="sxs-lookup"><span data-stu-id="35835-119">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="35835-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="35835-120">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
