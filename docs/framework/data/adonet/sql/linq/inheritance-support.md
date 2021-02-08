---
description: 'Daha fazla bilgi edinin: devralma desteği'
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: ff6956441ab72f720151e42bd9358c8df1170e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803873"
---
# <a name="inheritance-support"></a><span data-ttu-id="11e84-103">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="11e84-103">Inheritance Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="11e84-104">*tek tablo eşlemeyi* destekler.</span><span class="sxs-lookup"><span data-stu-id="11e84-104">supports *single-table mapping*.</span></span> <span data-ttu-id="11e84-105">Diğer bir deyişle, tüm devralma hiyerarşisi tek bir veritabanı tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="11e84-105">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="11e84-106">Tablo, tüm hiyerarşinin tüm olası veri sütunlarının düzleştirilmiş birleşimini içerir.</span><span class="sxs-lookup"><span data-stu-id="11e84-106">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="11e84-107">(UNION, iki tablonun, özgün tablolardan birinde bulunan satırları içeren tek bir tabloda birleştirilmesinin sonucudur.) Her satırda, satır tarafından temsil edilen örneğin türüne uygulanmayan sütunlarda null değerler vardır.</span><span class="sxs-lookup"><span data-stu-id="11e84-107">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="11e84-108">Tek tablo eşleme stratejisi, devralmanın en basit gösterimidir ve birçok farklı sorgu kategorisi için iyi performans özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="11e84-108">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="11e84-109">Bu eşlemeyi ' de uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="11e84-109">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="11e84-110">Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="11e84-110">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="11e84-111">Visual Studio kullanan geliştiriciler, devralma hiyerarşileri eşlemek için Nesne İlişkisel Tasarımcısı da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="11e84-111">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e84-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11e84-112">See also</span></span>

- [<span data-ttu-id="11e84-113">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="11e84-113">Background Information</span></span>](background-information.md)
