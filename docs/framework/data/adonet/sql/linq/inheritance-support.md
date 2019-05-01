---
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033559"
---
# <a name="inheritance-support"></a><span data-ttu-id="1aed0-102">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="1aed0-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1aed0-103">destekleyen *tek tablo eşleme*.</span><span class="sxs-lookup"><span data-stu-id="1aed0-103">supports *single-table mapping*.</span></span> <span data-ttu-id="1aed0-104">Diğer bir deyişle, tam devralma hiyerarşisinde bir tek veritabanı tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="1aed0-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="1aed0-105">Tablo, hiyerarşinin tamamı için tüm olası veri sütunları düzleştirilmiş birleşimini içerir.</span><span class="sxs-lookup"><span data-stu-id="1aed0-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="1aed0-106">(Bir birleşim özgün tablolardan birini mevcut satırları içeren bir tabloya iki tabloyu birleştirerek sonucudur.) Her satır, satır tarafından temsil edilen örneği türü için geçerli olmayan sütunlardaki null değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1aed0-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="1aed0-107">Tek tablo eşleme stratejisi basit devralma gösterimi ve birçok farklı türdeki sorgular için iyi bir performans özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1aed0-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="1aed0-108">Bu eşleme içinde uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], devralma hiyerarşisi kök sınıfında öznitelik özellikleri ve öznitelikler belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1aed0-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="1aed0-109">Daha fazla bilgi için [nasıl yapılır: Devralma hiyerarşilerini eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="1aed0-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="1aed0-110">Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşilerini eşleme için.</span><span class="sxs-lookup"><span data-stu-id="1aed0-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aed0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aed0-111">See also</span></span>

- [<span data-ttu-id="1aed0-112">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="1aed0-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
