---
title: Devralma desteği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 7633ba80d2657f2f0135ee702a6cc89a260fec68
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="inheritance-support"></a><span data-ttu-id="38827-102">Devralma desteği</span><span class="sxs-lookup"><span data-stu-id="38827-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="38827-103"> destekleyen *tek tablo eşlemesi*.</span><span class="sxs-lookup"><span data-stu-id="38827-103"> supports *single-table mapping*.</span></span> <span data-ttu-id="38827-104">Diğer bir deyişle, bir tam devralma hiyerarşisi tek veritabanı tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="38827-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="38827-105">Tablo tüm hiyerarşinin tüm olası veri sütunlarını düzleştirilmiş birleşimini içerir.</span><span class="sxs-lookup"><span data-stu-id="38827-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="38827-106">(Bir birleşimi olan özgün tablolardan birini mevcut satırlar bir tabloya iki tablo birleştirme sonucudur.) Her satır satır tarafından temsil edilen örnek türü için geçerli olmayan sütun null değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="38827-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="38827-107">Tek tablo eşleme stratejisi devralma basit gösterimini ve birçok farklı türdeki sorgular için iyi performans özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="38827-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="38827-108">Bu eşleme uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], öznitelikleri ve öznitelik özellikleri Devralma Hiyerarşisi kök sınıfının belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38827-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="38827-109">Daha fazla bilgi için bkz: [nasıl yapılır: eşleme devralma hiyerarşileri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="38827-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="38827-110">Geliştiriciler Visual Studio kullanarak da kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşileri eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="38827-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38827-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38827-111">See Also</span></span>  
 [<span data-ttu-id="38827-112">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="38827-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
