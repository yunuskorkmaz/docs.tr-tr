---
title: Modelleme ve Eşleme
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 5592ce5301216c8c3e74231480997d9e44d71a7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197761"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="cba24-102">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="cba24-102">Modeling and Mapping</span></span>

<span data-ttu-id="cba24-103">Entity Framework kavramsal modeli, depolama modelini ve bu iki arasındaki eşlemeyi uygulamanıza en uygun şekilde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba24-103">In the Entity Framework, you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="cba24-104">Visual Studio 'daki Varlık Veri Modeli araçları, oluşturmanıza izin verir. bir veritabanından veya bir grafik modelden [edmx dosyası](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) ve sonra veritabanı ya da model değiştiğinde bu dosyayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="cba24-104">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="cba24-105">Entity Framework 4,1 ' den başlayarak, Code First geliştirmeyi kullanarak programlı bir şekilde model de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba24-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="cba24-106">Code First geliştirmesi için iki farklı senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="cba24-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="cba24-107">Her iki durumda da geliştirici, .NET Framework sınıf tanımlarını kodlayarak bir model tanımlar ve isteğe bağlı olarak, veri açıklamalarını veya Fluent API kullanarak ek eşleme veya yapılandırma belirtir.</span><span class="sxs-lookup"><span data-stu-id="cba24-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="cba24-108">Daha fazla bilgi için bkz. [model oluşturma](/ef/ef6/modeling/).</span><span class="sxs-lookup"><span data-stu-id="cba24-108">For more information, see [Creating a Model](/ef/ef6/modeling/).</span></span>  
  
 <span data-ttu-id="cba24-109">Ayrıca, .NET Framework dahil edilen EDM oluşturucuyu de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba24-109">You can also use the EDM Generator, which is included with the .NET Framework.</span></span> <span data-ttu-id="cba24-110">EdmGen.exe var olan bir veri kaynağından. csdl,. ssdl ve. MSL dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba24-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="cba24-111">Ayrıca modeli ve eşleme içeriğini el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba24-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="cba24-112">Daha fazla bilgi için bkz. [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cba24-112">For more information, see [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).</span></span>
