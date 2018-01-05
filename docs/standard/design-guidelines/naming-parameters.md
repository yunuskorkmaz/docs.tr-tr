---
title: "Adlandırma parametreleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a10fa8835bfbcf826f8a3bb9318966e0dc603864
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-parameters"></a><span data-ttu-id="32f35-102">Adlandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="32f35-102">Naming Parameters</span></span>
<span data-ttu-id="32f35-103">Okunabilirlik belirgin nedenini görsel Tasarım araçları IntelliSense ve işlevsellik gözatma sınıfı sağladığınızda parametreleri belgelerinde ve Tasarımcısı'nda görüntülendiğinden yönergelere parametre adları için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="32f35-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="32f35-104">**✓ YAPMAK** camelCasing parametre adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="32f35-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="32f35-105">**✓ YAPMAK** açıklayıcı parametre adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="32f35-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="32f35-106">**✓ DÜŞÜNÜN** parametrenin türü yerine bir parametrenin anlamı dayalı adları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="32f35-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="32f35-107">İşleç aşırı yüklemesi parametreleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="32f35-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="32f35-108">**✓ YAPMAK** kullanmak `left` ve `right` parametreleri için hiçbir anlamı ise ikili İşleç aşırı yüklemesi parametre adları için.</span><span class="sxs-lookup"><span data-stu-id="32f35-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="32f35-109">**✓ YAPMAK** kullanmak `value` için birli işleç aşırı yüklemesi parametre adları parametreleri için hiçbir anlamı ise.</span><span class="sxs-lookup"><span data-stu-id="32f35-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="32f35-110">**✓ DÜŞÜNÜN** anlamlı adlar işleci aşırı yükleme parametreleri bunun nedenle önemli değer eklerse.</span><span class="sxs-lookup"><span data-stu-id="32f35-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="32f35-111">**X yok** kullanım kısaltmalar veya sayısal dizinlerini işleci için aşırı yükleme parametre adları.</span><span class="sxs-lookup"><span data-stu-id="32f35-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="32f35-112">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="32f35-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="32f35-113">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="32f35-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f35-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32f35-114">See Also</span></span>  
 [<span data-ttu-id="32f35-115">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="32f35-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="32f35-116">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="32f35-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
