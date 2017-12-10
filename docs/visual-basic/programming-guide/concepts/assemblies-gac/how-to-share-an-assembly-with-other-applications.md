---
title: "Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ad7a3f2ee82d0a582e755035448d565a9a8cb9d
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="5620c-102">Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma</span><span class="sxs-lookup"><span data-stu-id="5620c-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="5620c-103">Derlemeler, özel veya paylaşılan olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılması amaçlanmıştır değil çünkü basit programlarının çoğu özel bir derlemenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="5620c-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="5620c-104">Bir derlemeyi başka uygulamalarla paylaşma için onu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="5620c-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="5620c-105">Bir derlemeyi paylaşımı</span><span class="sxs-lookup"><span data-stu-id="5620c-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="5620c-106">Derlemenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5620c-106">Create your assembly.</span></span> <span data-ttu-id="5620c-107">Daha fazla bilgi için bkz: [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5620c-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="5620c-108">Güçlü bir ad, derlemenizi atayın.</span><span class="sxs-lookup"><span data-stu-id="5620c-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="5620c-109">Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="5620c-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="5620c-110">Sürüm bilgileri, derlemenizi atayın.</span><span class="sxs-lookup"><span data-stu-id="5620c-110">Assign version information to your assembly.</span></span> <span data-ttu-id="5620c-111">Daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="5620c-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="5620c-112">Derleme genel derleme önbelleğine ekleme.</span><span class="sxs-lookup"><span data-stu-id="5620c-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="5620c-113">Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="5620c-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="5620c-114">Diğer uygulamalardan derlemesinde bulunan türleri erişin.</span><span class="sxs-lookup"><span data-stu-id="5620c-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="5620c-115">Daha fazla bilgi için bkz: [nasıl yapılır: bir Strong-Named derleme başvurusu](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="5620c-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5620c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5620c-116">See Also</span></span>  
 <span data-ttu-id="5620c-117">[Programlama kavramları](../../../../visual-basic/programming-guide/concepts/index.md) [derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="5620c-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="5620c-118">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="5620c-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
