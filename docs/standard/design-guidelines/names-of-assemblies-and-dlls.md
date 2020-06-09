---
title: Bütünleştirilmiş Kod ve DLL Adları
description: Adlandırma derlemeleri ve dinamik bağlantı kitaplıkları (dll 'Ler) için kılavuz bilgi edinin. Bir derleme bir veya daha fazla dosyaya yayılabilir, ancak genellikle bir DLL ile bire bir eşler.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: de7ce3ee774d4598521d7156d0d660c3fe30154c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594484"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="f3185-104">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="f3185-104">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="f3185-105">Derleme, yönetilen kod programlarının dağıtım ve kimlik birimidir.</span><span class="sxs-lookup"><span data-stu-id="f3185-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="f3185-106">Derlemeler bir veya daha fazla dosyaya yayılabilse de, genellikle bir derleme DLL ile bire bir eşler.</span><span class="sxs-lookup"><span data-stu-id="f3185-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="f3185-107">Bu nedenle, bu bölümde yalnızca DLL adlandırma kuralları açıklanmakta ve bu daha sonra derleme adlandırma kurallarına eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f3185-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="f3185-108">✔️, System. Data gibi büyük işlevsellik öbeklerini öneren derleme dll 'lerinizin adlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="f3185-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="f3185-109">Derleme ve DLL adlarının ad alanı adlarına karşılık gelmesi gerekmez, ancak derlemeleri adlandırırken ad alanı adını izlemek mantıklı değildir.</span><span class="sxs-lookup"><span data-stu-id="f3185-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="f3185-110">Parmak izi iyi bir kuralı, derlemede bulunan ad alanlarının ortak ön ekine göre DLL 'yi adlandırma.</span><span class="sxs-lookup"><span data-stu-id="f3185-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="f3185-111">Örneğin, iki ad alanı olan bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature` , çağrılabilir `MyCompany.MyTechnology.dll` .</span><span class="sxs-lookup"><span data-stu-id="f3185-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="f3185-112">✔️ Dll 'Leri aşağıdaki modele göre adlandırmayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="f3185-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="f3185-113">Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce bulunur.</span><span class="sxs-lookup"><span data-stu-id="f3185-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="f3185-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f3185-114">For example:</span></span>

 <span data-ttu-id="f3185-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="f3185-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="f3185-116">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f3185-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f3185-117">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="f3185-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f3185-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3185-118">See also</span></span>

- [<span data-ttu-id="f3185-119">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f3185-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f3185-120">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f3185-120">Naming Guidelines</span></span>](naming-guidelines.md)
