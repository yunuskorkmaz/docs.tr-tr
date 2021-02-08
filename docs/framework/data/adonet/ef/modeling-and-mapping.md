---
description: 'Daha fazla bilgi edinin: modelleme ve eşleme'
title: Modelleme ve Eşleme
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 063cac072b7a205a471cd808fc85ad9a3ac71288
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795007"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="b6180-103">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="b6180-103">Modeling and Mapping</span></span>

<span data-ttu-id="b6180-104">Entity Framework kavramsal modeli, depolama modelini ve bu iki arasındaki eşlemeyi uygulamanıza en uygun şekilde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6180-104">In the Entity Framework, you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="b6180-105">Visual Studio 'daki Varlık Veri Modeli araçları, oluşturmanıza izin verir. bir veritabanından veya bir grafik modelden [edmx dosyası](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) ve sonra veritabanı ya da model değiştiğinde bu dosyayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b6180-105">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="b6180-106">Entity Framework 4,1 ' den başlayarak, Code First geliştirmeyi kullanarak programlı bir şekilde model de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6180-106">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="b6180-107">Code First geliştirmesi için iki farklı senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="b6180-107">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="b6180-108">Her iki durumda da geliştirici, .NET Framework sınıf tanımlarını kodlayarak bir model tanımlar ve isteğe bağlı olarak, veri açıklamalarını veya Fluent API kullanarak ek eşleme veya yapılandırma belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6180-108">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="b6180-109">Daha fazla bilgi için bkz. [model oluşturma](/ef/ef6/modeling/).</span><span class="sxs-lookup"><span data-stu-id="b6180-109">For more information, see [Creating a Model](/ef/ef6/modeling/).</span></span>  
  
 <span data-ttu-id="b6180-110">Ayrıca, .NET Framework dahil edilen EDM oluşturucuyu de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6180-110">You can also use the EDM Generator, which is included with the .NET Framework.</span></span> <span data-ttu-id="b6180-111">EdmGen.exe var olan bir veri kaynağından. csdl,. ssdl ve. MSL dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6180-111">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="b6180-112">Ayrıca modeli ve eşleme içeriğini el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6180-112">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="b6180-113">Daha fazla bilgi için bkz. [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b6180-113">For more information, see [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).</span></span>
