---
title: "Modelleme ve eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 82bb3ca8bd5ef0659bbb222753b3225288fcbcfc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="56fd4-102">Modelleme ve eşleme</span><span class="sxs-lookup"><span data-stu-id="56fd4-102">Modeling and Mapping</span></span>
<span data-ttu-id="56fd4-103">İçinde [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]tanımlayabilirsiniz kavramsal model, depolama modelindeki ve uygulamanızı en iyi iki şekilde arasında eşleme uygun.</span><span class="sxs-lookup"><span data-stu-id="56fd4-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="56fd4-104">Varlık veri modeli Araçları [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] oluşturmanızı sağlayan bir.[ sistemin edmx dosyası](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) bir veritabanı veya bir grafik modeli ve ardından güncelleştirme veritabanı veya model değiştiğinde, dosya.</span><span class="sxs-lookup"><span data-stu-id="56fd4-104">The Entity Data Model Tools in [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] allow you to create an .[edmx file](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="56fd4-105">Entity Framework 4.1 ile başlayarak, Code First geliştirme kullanarak programlı olarak bir modeli de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56fd4-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="56fd4-106">Code First geliştirme için iki farklı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="56fd4-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="56fd4-107">Her iki durumda da Geliştirici .NET Framework sınıf tanımları kodlayarak bir model tanımlar ve ardından isteğe bağlı olarak ek eşleme veya yapılandırma veri ek açıklamaları veya fluent API kullanılarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="56fd4-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="56fd4-108">Daha fazla bilgi için bkz: [oluşturma ve kavramsal Model eşleme](http://go.microsoft.com/fwlink/?LinkId=235016).</span><span class="sxs-lookup"><span data-stu-id="56fd4-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="56fd4-109">İle birlikte EDM Oluşturucu de kullanabilirsiniz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56fd4-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="56fd4-110">EdmGen.exe .csdl .ssdl .msl dosyaları ve varolan bir veri kaynağından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56fd4-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="56fd4-111">İçerik eşleme ve model el ile de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56fd4-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="56fd4-112">Daha fazla bilgi için bkz: [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="56fd4-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
