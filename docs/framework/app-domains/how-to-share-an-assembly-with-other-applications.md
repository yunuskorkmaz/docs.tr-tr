---
title: 'Nasıl yapılır: Bir bütünleştirilmiş kodu başka uygulamalarla paylaşma'
description: Bkz. .NET 'teki diğer uygulamalarla bir derlemeyi paylaşma. Derlemeler özel (varsayılan) veya paylaşılan olabilir. Bir derlemeyi paylaşmak için GAC 'ye yerleştirin.
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242545"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="fffe4-105">Nasıl yapılır: Bir bütünleştirilmiş kodu başka uygulamalarla paylaşma</span><span class="sxs-lookup"><span data-stu-id="fffe4-105">How to: Share an assembly with other applications</span></span>

<span data-ttu-id="fffe4-106">Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="fffe4-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="fffe4-107">Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği 'ne (GAC)](gac.md)yerleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fffe4-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="fffe4-108">Bir derlemeyi paylaşmak için:</span><span class="sxs-lookup"><span data-stu-id="fffe4-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="fffe4-109">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fffe4-109">Create your assembly.</span></span> <span data-ttu-id="fffe4-110">Daha fazla bilgi için bkz. [derlemeler oluşturma](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="fffe4-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="fffe4-111">Derlemenize tanımlayıcı bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="fffe4-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="fffe4-112">Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="fffe4-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="fffe4-113">Derlemenizin sürüm bilgilerini atayın.</span><span class="sxs-lookup"><span data-stu-id="fffe4-113">Assign version information to your assembly.</span></span> <span data-ttu-id="fffe4-114">Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="fffe4-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="fffe4-115">Derlemenizi genel derleme önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fffe4-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="fffe4-116">Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="fffe4-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="fffe4-117">Diğer uygulamalardan derlemede bulunan türlere erişin.</span><span class="sxs-lookup"><span data-stu-id="fffe4-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="fffe4-118">Daha fazla bilgi için bkz. [nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="fffe4-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffe4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fffe4-119">See also</span></span>

- [<span data-ttu-id="fffe4-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fffe4-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="fffe4-121">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fffe4-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="fffe4-122">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="fffe4-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
