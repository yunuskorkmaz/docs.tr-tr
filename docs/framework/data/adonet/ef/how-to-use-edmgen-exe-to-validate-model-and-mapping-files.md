---
title: "Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları doğrulamak için kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3ae17ceccf9d452951b1332525f3fa3536fd344c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="e67b2-102">Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları doğrulamak için kullanın</span><span class="sxs-lookup"><span data-stu-id="e67b2-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="e67b2-103">Bu konuda nasıl kullanılacağını gösterir [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) modeli ve eşleme dosyaları doğrulamak için aracı.</span><span class="sxs-lookup"><span data-stu-id="e67b2-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="e67b2-104">Daha fazla bilgi için bkz: [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="e67b2-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="e67b2-105">EdmGen.exe kullanarak Okul modeli doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="e67b2-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="e67b2-106">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e67b2-106">Create the School database.</span></span> <span data-ttu-id="e67b2-107">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="e67b2-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="e67b2-108">Okul modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e67b2-108">Generate the School model.</span></span> <span data-ttu-id="e67b2-109">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="e67b2-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="e67b2-110">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e67b2-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e67b2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e67b2-111">See Also</span></span>  
 [<span data-ttu-id="e67b2-112">Nasıl yapılır: bir Entity Framework projesi el ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e67b2-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="e67b2-113">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="e67b2-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="e67b2-114">Nasıl yapılır: sorgu performansını artırmak için görünümlerini önceden oluşturmak</span><span class="sxs-lookup"><span data-stu-id="e67b2-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="e67b2-115">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e67b2-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
