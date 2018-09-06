---
title: 'Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738226"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="3cbbc-102">Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma</span><span class="sxs-lookup"><span data-stu-id="3cbbc-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="3cbbc-103">Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="3cbbc-104">Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="3cbbc-105">Derlemeyi paylaşmanız</span><span class="sxs-lookup"><span data-stu-id="3cbbc-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="3cbbc-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-106">Create your assembly.</span></span> <span data-ttu-id="3cbbc-107">Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="3cbbc-108">Bir derlemeye güçlü bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="3cbbc-109">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="3cbbc-110">Sürüm bilgileri için bir derleme atayın.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-110">Assign version information to your assembly.</span></span> <span data-ttu-id="3cbbc-111">Daha fazla bilgi için [derleme sürümlendirme](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="3cbbc-112">Derlemenizi, Genel Derleme Önbelleği'ne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="3cbbc-113">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="3cbbc-114">Diğer uygulamalardan derlemesinde bulunan türleri erişin.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="3cbbc-115">Daha fazla bilgi için [nasıl yapılır: bir Strong-Named derleme başvurusu](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="3cbbc-115">For more information, see [How to: Reference a Strong-Named Assembly](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbbc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cbbc-116">See Also</span></span>  
 <span data-ttu-id="3cbbc-117">[Programlama kavramları](../../../../visual-basic/programming-guide/concepts/index.md) [derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="3cbbc-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="3cbbc-118">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="3cbbc-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
