---
title: 'Nasıl yapılır: bir derlemeyi diğer uygulamalarla paylaşma'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644287"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="19f95-102">Nasıl yapılır: bir derlemeyi diğer uygulamalarla paylaşma</span><span class="sxs-lookup"><span data-stu-id="19f95-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="19f95-103">Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="19f95-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="19f95-104">Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği 'ne (GAC)](gac.md)yerleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="19f95-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="19f95-105">Bir derlemeyi paylaşmak için:</span><span class="sxs-lookup"><span data-stu-id="19f95-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="19f95-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19f95-106">Create your assembly.</span></span> <span data-ttu-id="19f95-107">Daha fazla bilgi için bkz. [derlemeler oluşturma](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="19f95-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="19f95-108">Derlemenize tanımlayıcı bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="19f95-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="19f95-109">Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="19f95-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="19f95-110">Derlemenizin sürüm bilgilerini atayın.</span><span class="sxs-lookup"><span data-stu-id="19f95-110">Assign version information to your assembly.</span></span> <span data-ttu-id="19f95-111">Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="19f95-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="19f95-112">Derlemenizi genel derleme önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19f95-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="19f95-113">Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="19f95-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="19f95-114">Diğer uygulamalardan derlemede bulunan türlere erişin.</span><span class="sxs-lookup"><span data-stu-id="19f95-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="19f95-115">Daha fazla bilgi için bkz. [nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="19f95-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f95-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19f95-116">See also</span></span>

- [<span data-ttu-id="19f95-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="19f95-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="19f95-118">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19f95-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="19f95-119">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="19f95-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
