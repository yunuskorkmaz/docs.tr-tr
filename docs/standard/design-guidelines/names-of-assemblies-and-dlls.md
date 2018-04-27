---
title: Derlemeler ve DLL adları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ff14d3d804329e591486a7eb2a2ee7ed430f622c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="dca2e-102">Derlemeler ve DLL adları</span><span class="sxs-lookup"><span data-stu-id="dca2e-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="dca2e-103">Derleme dağıtımı ve yönetilen kod programlar kimliğini birimidir.</span><span class="sxs-lookup"><span data-stu-id="dca2e-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="dca2e-104">Genellikle bir veya daha çok dosya derlemeleri yayılabilir karşın, bir derlemeyi bire bir DLL ile eşler.</span><span class="sxs-lookup"><span data-stu-id="dca2e-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="dca2e-105">Bu nedenle, bu bölümde daha sonra derleme adlandırma kurallarına eşlenen yalnızca DLL adlandırma kuralları, açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dca2e-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="dca2e-106">**✓ YAPMAK** derlemenizi System.Data gibi işlevleri büyük boyutta önermek DLL'ler için adları'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dca2e-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="dca2e-107">Derleme ve DLL adları ad alanı adları için karşılık gelen gerekmez, ancak ad derlemeleri adlandırırken izlemek makul.</span><span class="sxs-lookup"><span data-stu-id="dca2e-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="dca2e-108">Bir iyi derlemesinde bulunan ad alanları ortak önekini temel DLL adlandırmak için udur.</span><span class="sxs-lookup"><span data-stu-id="dca2e-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="dca2e-109">Örneğin, iki ad alanı, bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`, çağrılabilir `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="dca2e-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="dca2e-110">**✓ DÜŞÜNÜN** göre aşağıdaki düzeni DLL'leri adlandırma:</span><span class="sxs-lookup"><span data-stu-id="dca2e-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="dca2e-111">Burada `<Component>` bir veya daha fazla nokta ayrılmış yan tümceleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dca2e-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="dca2e-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dca2e-112">For example:</span></span>  
  
 <span data-ttu-id="dca2e-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="dca2e-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="dca2e-114">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="dca2e-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dca2e-115">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="dca2e-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca2e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dca2e-116">See Also</span></span>  
 [<span data-ttu-id="dca2e-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dca2e-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="dca2e-118">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="dca2e-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
