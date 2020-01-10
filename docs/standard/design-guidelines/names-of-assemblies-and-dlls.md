---
title: Bütünleştirilmiş Kod ve DLL Adları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: eebccba0b923b04333f289a85330d190c31013ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709263"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="454c5-102">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="454c5-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="454c5-103">Derleme, yönetilen kod programlarının dağıtım ve kimlik birimidir.</span><span class="sxs-lookup"><span data-stu-id="454c5-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="454c5-104">Derlemeler bir veya daha fazla dosyaya yayılabilse de, genellikle bir derleme DLL ile bire bir eşler.</span><span class="sxs-lookup"><span data-stu-id="454c5-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="454c5-105">Bu nedenle, bu bölümde yalnızca DLL adlandırma kuralları açıklanmakta ve bu daha sonra derleme adlandırma kurallarına eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="454c5-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="454c5-106">**✓ DO** derlemenizi System.Data gibi işlevleri büyük boyutta önermek DLL'ler için adları'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="454c5-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="454c5-107">Derleme ve DLL adlarının ad alanı adlarına karşılık gelmesi gerekmez, ancak derlemeleri adlandırırken ad alanı adını izlemek mantıklı değildir.</span><span class="sxs-lookup"><span data-stu-id="454c5-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="454c5-108">Parmak izi iyi bir kuralı, derlemede bulunan ad alanlarının ortak ön ekine göre DLL 'yi adlandırma.</span><span class="sxs-lookup"><span data-stu-id="454c5-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="454c5-109">Örneğin, `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`iki ad alanı olan bir derleme `MyCompany.MyTechnology.dll`çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="454c5-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="454c5-110">**✓ CONSIDER** göre aşağıdaki düzeni DLL'leri adlandırma:</span><span class="sxs-lookup"><span data-stu-id="454c5-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="454c5-111">Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce içerir.</span><span class="sxs-lookup"><span data-stu-id="454c5-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="454c5-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="454c5-112">For example:</span></span>  
  
 <span data-ttu-id="454c5-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="454c5-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="454c5-114">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="454c5-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="454c5-115">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="454c5-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454c5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="454c5-116">See also</span></span>

- [<span data-ttu-id="454c5-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="454c5-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="454c5-118">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="454c5-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
