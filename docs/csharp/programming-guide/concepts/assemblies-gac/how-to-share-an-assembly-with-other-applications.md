---
title: 'Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595737"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="03872-102">Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma (C#)</span><span class="sxs-lookup"><span data-stu-id="03872-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="03872-103">Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="03872-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="03872-104">Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği](../../../../framework/app-domains/gac.md) 'ne (GAC) yerleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="03872-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="03872-105">Bir derlemeyi paylaşma</span><span class="sxs-lookup"><span data-stu-id="03872-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="03872-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="03872-106">Create your assembly.</span></span> <span data-ttu-id="03872-107">Daha fazla bilgi için bkz. [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="03872-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="03872-108">Derlemenize tanımlayıcı bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="03872-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="03872-109">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi güçlü bir adla](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)imzalayın.</span><span class="sxs-lookup"><span data-stu-id="03872-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="03872-110">Derlemenizin sürüm bilgilerini atayın.</span><span class="sxs-lookup"><span data-stu-id="03872-110">Assign version information to your assembly.</span></span> <span data-ttu-id="03872-111">Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="03872-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="03872-112">Derlemenizi genel derleme önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03872-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="03872-113">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="03872-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="03872-114">Diğer uygulamalardan derlemede bulunan türlere erişin.</span><span class="sxs-lookup"><span data-stu-id="03872-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="03872-115">Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı bir derlemeye](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)başvuru yapın.</span><span class="sxs-lookup"><span data-stu-id="03872-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03872-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03872-116">See also</span></span>

- [<span data-ttu-id="03872-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03872-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="03872-118">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="03872-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
