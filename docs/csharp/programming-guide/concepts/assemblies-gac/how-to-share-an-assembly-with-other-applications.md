---
title: 'Nasıl yapılır: Bir derlemeyi başka uygulamalarla paylaşma (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314795"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="4a3ac-102">Nasıl yapılır: Bir derlemeyi başka uygulamalarla paylaşma (C#)</span><span class="sxs-lookup"><span data-stu-id="4a3ac-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="4a3ac-103">Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="4a3ac-104">Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="4a3ac-105">Derlemeyi paylaşmanız</span><span class="sxs-lookup"><span data-stu-id="4a3ac-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="4a3ac-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-106">Create your assembly.</span></span> <span data-ttu-id="4a3ac-107">Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="4a3ac-108">Bir derlemeye güçlü bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="4a3ac-109">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="4a3ac-110">Sürüm bilgileri için bir derleme atayın.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-110">Assign version information to your assembly.</span></span> <span data-ttu-id="4a3ac-111">Daha fazla bilgi için [derleme sürümlendirme](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="4a3ac-112">Derlemenizi, Genel Derleme Önbelleği'ne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="4a3ac-113">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="4a3ac-114">Diğer uygulamalardan derlemesinde bulunan türleri erişin.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="4a3ac-115">Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı bir derlemeye başvuru](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ac-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3ac-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a3ac-116">See also</span></span>

- [<span data-ttu-id="4a3ac-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a3ac-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4a3ac-118">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="4a3ac-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
