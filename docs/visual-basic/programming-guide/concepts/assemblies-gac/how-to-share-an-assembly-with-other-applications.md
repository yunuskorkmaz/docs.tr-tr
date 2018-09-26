---
title: 'Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 3d29a3558a64c02fc8c59035f2fee5c64c4a776f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089418"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="dec2a-102">Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma</span><span class="sxs-lookup"><span data-stu-id="dec2a-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="dec2a-103">Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="dec2a-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="dec2a-104">Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="dec2a-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="dec2a-105">Derlemeyi paylaşmanız</span><span class="sxs-lookup"><span data-stu-id="dec2a-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="dec2a-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dec2a-106">Create your assembly.</span></span> <span data-ttu-id="dec2a-107">Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dec2a-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="dec2a-108">Bir derlemeye güçlü bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="dec2a-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="dec2a-109">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dec2a-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="dec2a-110">Sürüm bilgileri için bir derleme atayın.</span><span class="sxs-lookup"><span data-stu-id="dec2a-110">Assign version information to your assembly.</span></span> <span data-ttu-id="dec2a-111">Daha fazla bilgi için [derleme sürümlendirme](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="dec2a-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="dec2a-112">Derlemenizi, Genel Derleme Önbelleği'ne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dec2a-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="dec2a-113">Daha fazla bilgi için [nasıl yapılır: bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="dec2a-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="dec2a-114">Diğer uygulamalardan derlemesinde bulunan türleri erişin.</span><span class="sxs-lookup"><span data-stu-id="dec2a-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="dec2a-115">Daha fazla bilgi için [nasıl yapılır: bir Strong-Named derleme başvurusu](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="dec2a-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec2a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dec2a-116">See also</span></span>

- [<span data-ttu-id="dec2a-117">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="dec2a-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="dec2a-118">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dec2a-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="dec2a-119">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="dec2a-119">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
