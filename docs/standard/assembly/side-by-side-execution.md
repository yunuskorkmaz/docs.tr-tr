---
title: Derlemeler ve yan yana yürütme
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138650"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="3cc42-102">Derlemeler ve yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="3cc42-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="3cc42-103">Yan yana yürütme, aynı bilgisayarda bir uygulama veya bileşenin birden çok sürümünü saklama ve yürütme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="3cc42-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="3cc42-104">Bu da ortak dil çalışma zamanı sürümünün birden çok sürümünün ve çalışma zamanının bir sürümünü kullanan uygulama ve bileşenlerin birden çok sürümünün bir bilgisayar üzerinde aynı anda bulunabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3cc42-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="3cc42-105">Yan yana yürütme olanağı, bir uygulamanın bir bileşenin hangi sürümüne bağlanacağını ve bir uygulamanın hangi çalışma zamanını kullanacağı konusunda daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cc42-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="3cc42-106">Aynı derlemenin farklı sürümlerinin yan yana depolanması ve yürütülmesi için sunulan destek, tanımlayıcı adlandırmanın temel bir parçasıdır ve çalışma zamanının altyapısında yerleşik olarak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cc42-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="3cc42-107">Tanımlayıcı ada sahip olan derlemenin sürüm numarası kimliğinin bir parçası olduğundan, çalışma zamanı aynı derlemenin birden çok sürümünü genel derleme önbelleğinde tutabilir ve çalışma zamanında bu derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3cc42-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="3cc42-108">Çalışma zamanı size yan yana uygulamalar oluşturma olanağı sağlasa da yan yana yürütme otomatik değildir.</span><span class="sxs-lookup"><span data-stu-id="3cc42-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="3cc42-109">Yan yana yürütme için uygulama oluşturma hakkında daha fazla bilgi [için, yan yana yürütme için bileşenler oluşturmak için Yönergeler'e](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3cc42-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc42-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cc42-110">See also</span></span>

- [<span data-ttu-id="3cc42-111">Çalışma zamanı derlemeleri nasıl bulur?</span><span class="sxs-lookup"><span data-stu-id="3cc42-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="3cc42-112">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="3cc42-112">Assemblies in .NET</span></span>](index.md)
