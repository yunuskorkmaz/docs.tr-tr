---
title: Adlandırma parametreleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 35965f03f5c50cbe3ffcc9bdb615d99c50fc30a2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147924"
---
# <a name="naming-parameters"></a><span data-ttu-id="70076-102">Adlandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="70076-102">Naming Parameters</span></span>
<span data-ttu-id="70076-103">Okunabilirlik belirgin nedenini görsel tasarım araçlarını, IntelliSense ve gözatma işlevselliği sınıf sağladığınızda parametreleri belgelerinde ve Tasarımcısı'nda görüntülenen olduğundan, parametre isimleri için yönergeleri izlemeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="70076-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="70076-104">**✓ DO** camelCasing parametre adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="70076-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="70076-105">**✓ DO** açıklayıcı parametre adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="70076-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="70076-106">**✓ CONSIDER** parametrenin türü yerine bir parametrenin anlamı dayalı adları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="70076-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="70076-107">Adlandırma işleci aşırı yükleme parametreleri</span><span class="sxs-lookup"><span data-stu-id="70076-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="70076-108">**✓ DO** kullanmak `left` ve `right` parametreleri için hiçbir anlamı ise ikili İşleç aşırı yüklemesi parametre adları için.</span><span class="sxs-lookup"><span data-stu-id="70076-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="70076-109">**✓ DO** kullanmak `value` için birli işleç aşırı yüklemesi parametre adları parametreleri için hiçbir anlamı ise.</span><span class="sxs-lookup"><span data-stu-id="70076-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="70076-110">**✓ CONSIDER** anlamlı adlar işleci aşırı yükleme parametreleri bunun nedenle önemli değer eklerse.</span><span class="sxs-lookup"><span data-stu-id="70076-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="70076-111">**X DO NOT** kullanım kısaltmalar veya sayısal dizinlerini işleci için aşırı yükleme parametre adları.</span><span class="sxs-lookup"><span data-stu-id="70076-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="70076-112">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="70076-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="70076-113">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="70076-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70076-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70076-114">See also</span></span>

- [<span data-ttu-id="70076-115">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="70076-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="70076-116">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="70076-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
