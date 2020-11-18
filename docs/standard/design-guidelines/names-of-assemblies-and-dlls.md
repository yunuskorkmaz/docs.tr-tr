---
title: Bütünleştirilmiş Kod ve DLL Adları
description: Adlandırma derlemeleri ve dinamik bağlantı kitaplıkları (dll 'Ler) için kılavuz bilgi edinin. Bir derleme bir veya daha fazla dosyaya yayılabilir, ancak genellikle bir DLL ile bire bir eşler.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 2d1484889eb7db537de970c31109f26a6d61ad8d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830057"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="8c35f-104">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="8c35f-104">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="8c35f-105">Derleme, yönetilen kod programlarının dağıtım ve kimlik birimidir.</span><span class="sxs-lookup"><span data-stu-id="8c35f-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="8c35f-106">Derlemeler bir veya daha fazla dosyaya yayılabilse de, genellikle bir derleme DLL ile bire bir eşler.</span><span class="sxs-lookup"><span data-stu-id="8c35f-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="8c35f-107">Bu nedenle, bu bölümde yalnızca DLL adlandırma kuralları açıklanmakta ve bu daha sonra derleme adlandırma kurallarına eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8c35f-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="8c35f-108">✔️, System. Data gibi büyük işlevsellik öbeklerini öneren derleme dll 'lerinizin adlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="8c35f-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="8c35f-109">Derleme ve DLL adlarının ad alanı adlarına karşılık gelmesi gerekmez, ancak derlemeleri adlandırırken ad alanı adını izlemek mantıklı değildir.</span><span class="sxs-lookup"><span data-stu-id="8c35f-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="8c35f-110">Parmak izi iyi bir kuralı, derlemede bulunan ad alanlarının ortak ön ekine göre DLL 'yi adlandırma.</span><span class="sxs-lookup"><span data-stu-id="8c35f-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="8c35f-111">Örneğin, iki ad alanı olan bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature` , çağrılabilir `MyCompany.MyTechnology.dll` .</span><span class="sxs-lookup"><span data-stu-id="8c35f-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="8c35f-112">✔️ Dll 'Leri aşağıdaki modele göre adlandırmayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="8c35f-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="8c35f-113">Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c35f-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="8c35f-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8c35f-114">For example:</span></span>

 <span data-ttu-id="8c35f-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="8c35f-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="8c35f-116">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8c35f-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8c35f-117">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="8c35f-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8c35f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c35f-118">See also</span></span>

- [<span data-ttu-id="8c35f-119">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8c35f-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="8c35f-120">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8c35f-120">Naming Guidelines</span></span>](naming-guidelines.md)
