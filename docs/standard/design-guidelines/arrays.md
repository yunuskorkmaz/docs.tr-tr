---
title: Diziler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 30277507050091de6b1e9293401d61ac5e351a1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280627"
---
# <a name="arrays"></a><span data-ttu-id="c5723-102">Diziler</span><span class="sxs-lookup"><span data-stu-id="c5723-102">Arrays</span></span>
<span data-ttu-id="c5723-103">✔️ ortak API 'lerde diziler üzerinde koleksiyonları kullanmayı tercih eder.</span><span class="sxs-lookup"><span data-stu-id="c5723-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="c5723-104">[Koleksiyonlar](guidelines-for-collections.md) bölümü koleksiyonlar ve diziler arasında nasıl seçim yapılacağı hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5723-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="c5723-105">❌Salt okunurdur dizi alanlarını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c5723-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="c5723-106">Alanın kendisi salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5723-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="c5723-107">✔️ çok boyutlu diziler yerine pürüzlü Diziler kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c5723-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="c5723-108">Sivri dizi öğeleri de diziler olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="c5723-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="c5723-109">Öğeleri oluşturan diziler farklı boyutlarda olabilir ve çok boyutlu dizilere kıyasla bazı veri kümeleri (örn. seyrek matris) için daha az harcanan alana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5723-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="c5723-110">Ayrıca, CLR, basit diziler üzerinde dizin işlemlerini iyileştirir, bu nedenle bazı senaryolarda çalışma zamanı daha iyi bir performans sergilebilirler.</span><span class="sxs-lookup"><span data-stu-id="c5723-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="c5723-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="c5723-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c5723-112">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="c5723-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c5723-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5723-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="c5723-114">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c5723-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="c5723-115">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c5723-115">Usage Guidelines</span></span>](usage-guidelines.md)
