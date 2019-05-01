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
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945502"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="679c6-102">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="679c6-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="679c6-103">Bir derleme dağıtım ve yönetilen kod programları için kimlik birimidir.</span><span class="sxs-lookup"><span data-stu-id="679c6-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="679c6-104">Genellikle bir veya daha çok dosya derlemeleri yayılabilir olsa da, bir derleme bir DLL ile bire bir eşlenir.</span><span class="sxs-lookup"><span data-stu-id="679c6-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="679c6-105">Bu nedenle, bu bölümde olan derleme adlandırma kurallarına eşlenebilir yalnızca DLL adlandırma kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="679c6-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="679c6-106">**✓ DO** derlemenizi System.Data gibi işlevleri büyük boyutta önermek DLL'ler için adları'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="679c6-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="679c6-107">Bütünleştirilmiş kod ve DLL adları ad alanı adları için karşılık gelen gerekmez ancak ad alanı adı derlemelerini adlandırma izlenmesi gereken şüphelenilebilir.</span><span class="sxs-lookup"><span data-stu-id="679c6-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="679c6-108">Bir iyi derlemesinde bulunan ad alanlarının yaygın önekini temel DLL adı için udur.</span><span class="sxs-lookup"><span data-stu-id="679c6-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="679c6-109">Örneğin, iki ad alanı, bir derlemeye `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`, çağrılabilir `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="679c6-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="679c6-110">**✓ CONSIDER** göre aşağıdaki düzeni DLL'leri adlandırma:</span><span class="sxs-lookup"><span data-stu-id="679c6-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="679c6-111">Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce içeriyor.</span><span class="sxs-lookup"><span data-stu-id="679c6-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="679c6-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="679c6-112">For example:</span></span>  
  
 <span data-ttu-id="679c6-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="679c6-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="679c6-114">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="679c6-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="679c6-115">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="679c6-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679c6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="679c6-116">See also</span></span>

- [<span data-ttu-id="679c6-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="679c6-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="679c6-118">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="679c6-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
