---
title: 'Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: a5b20061c759fd914193f24aa123317f13d31dce
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266475"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="978af-102">Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma</span><span class="sxs-lookup"><span data-stu-id="978af-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="978af-103">Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="978af-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="978af-104">Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="978af-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="978af-105">Derlemeyi paylaşmanız</span><span class="sxs-lookup"><span data-stu-id="978af-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="978af-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="978af-106">Create your assembly.</span></span> <span data-ttu-id="978af-107">Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="978af-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="978af-108">Bir derlemeye güçlü bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="978af-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="978af-109">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="978af-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="978af-110">Sürüm bilgileri için bir derleme atayın.</span><span class="sxs-lookup"><span data-stu-id="978af-110">Assign version information to your assembly.</span></span> <span data-ttu-id="978af-111">Daha fazla bilgi için [derleme sürümlendirme](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="978af-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="978af-112">Derlemenizi, Genel Derleme Önbelleği'ne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="978af-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="978af-113">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="978af-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="978af-114">Diğer uygulamalardan derlemesinde bulunan türleri erişin.</span><span class="sxs-lookup"><span data-stu-id="978af-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="978af-115">Daha fazla bilgi için [nasıl yapılır: bir Strong-Named derleme başvurusu](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="978af-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978af-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="978af-116">See Also</span></span>

- [<span data-ttu-id="978af-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="978af-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="978af-118">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="978af-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
