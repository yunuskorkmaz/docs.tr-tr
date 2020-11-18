---
title: Adlandırma Parametreleri
description: Parametrelerin adlandırılmasıyla ilgili yönergeleri öğrenin. Örneğin, ortası büyük/küçük harf & açıklayıcı parametre adlarını kullanın &, tür yerine anlam temelinde adlandırmayı düşünün.
ms.date: 10/22/2008
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: b62cfbd58f671745054c557041e5d60af345c8d3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820845"
---
# <a name="naming-parameters"></a><span data-ttu-id="a4f90-104">Adlandırma Parametreleri</span><span class="sxs-lookup"><span data-stu-id="a4f90-104">Naming Parameters</span></span>
<span data-ttu-id="a4f90-105">Görsel tasarım araçları IntelliSense ve sınıf tarama işlevselliği sağladığınızda, bir okunabilirlik işleminin belirgin olmasının ötesinde parametre adları için yönergeleri izlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a4f90-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="a4f90-106">✔️ parametre adlarında Camelbüyük harfleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4f90-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="a4f90-107">✔️ tanımlayıcı parametre adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4f90-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="a4f90-108">✔️, parametre türü yerine parametrenin anlamı temelinde adları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a4f90-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="a4f90-109">Adlandırma Işleci aşırı yükleme parametreleri</span><span class="sxs-lookup"><span data-stu-id="a4f90-109">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="a4f90-110">`left`parametrelere bir anlamı yoksa `right` ikili işleç aşırı yüklemesi parametre adları için ve kullanın ✔️.</span><span class="sxs-lookup"><span data-stu-id="a4f90-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="a4f90-111">`value`parametrelere bir anlamı yoksa birli işleç aşırı yüklemesi parametre adları için ✔️ kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4f90-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="a4f90-112">✔️, işleç aşırı yükleme parametreleri için anlamlı adları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a4f90-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="a4f90-113">❌ İşleç aşırı yüklemesi parametre adları için kısaltmalar veya sayısal dizinler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a4f90-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="a4f90-114">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="a4f90-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a4f90-115">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="a4f90-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a4f90-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f90-116">See also</span></span>

- [<span data-ttu-id="a4f90-117">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a4f90-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a4f90-118">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a4f90-118">Naming Guidelines</span></span>](naming-guidelines.md)
