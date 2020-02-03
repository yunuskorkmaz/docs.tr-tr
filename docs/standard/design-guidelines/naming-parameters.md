---
title: Adlandırma Parametreleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743833"
---
# <a name="naming-parameters"></a><span data-ttu-id="f2172-102">Adlandırma Parametreleri</span><span class="sxs-lookup"><span data-stu-id="f2172-102">Naming Parameters</span></span>
<span data-ttu-id="f2172-103">Görsel tasarım araçları IntelliSense ve sınıf tarama işlevselliği sağladığınızda, bir okunabilirlik işleminin belirgin olmasının ötesinde parametre adları için yönergeleri izlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f2172-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="f2172-104">✔️ parametre adlarında Camelbüyük harfleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2172-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="f2172-105">✔️ tanımlayıcı parametre adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2172-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="f2172-106">✔️, parametre türü yerine parametrenin anlamı temelinde adları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f2172-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="f2172-107">Adlandırma Işleci aşırı yükleme parametreleri</span><span class="sxs-lookup"><span data-stu-id="f2172-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="f2172-108">✔️, parametrelere bir anlamı yoksa ikili işleç aşırı yüklemesi parametre adları için `left` ve `right` kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2172-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="f2172-109">parametrelere bir anlamı yoksa birli işleç aşırı yüklemesi parametre adları için `value` ✔️.</span><span class="sxs-lookup"><span data-stu-id="f2172-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="f2172-110">✔️, işleç aşırı yükleme parametreleri için anlamlı adları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f2172-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="f2172-111">❌ işleç aşırı yüklemesi parametre adları için kısaltmalar veya sayısal dizinler kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f2172-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="f2172-112">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f2172-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f2172-113">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="f2172-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f2172-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2172-114">See also</span></span>

- [<span data-ttu-id="f2172-115">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f2172-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f2172-116">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="f2172-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
