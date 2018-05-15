---
title: 'Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları doğrulamak için kullanın'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 197af6ae86de4057b864ef211c36f19aad83b003
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="36931-102">Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları doğrulamak için kullanın</span><span class="sxs-lookup"><span data-stu-id="36931-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="36931-103">Bu konuda nasıl kullanılacağını gösterir [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) modeli ve eşleme dosyaları doğrulamak için aracı.</span><span class="sxs-lookup"><span data-stu-id="36931-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="36931-104">Daha fazla bilgi için bkz: [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="36931-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="36931-105">EdmGen.exe kullanarak Okul modeli doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="36931-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="36931-106">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36931-106">Create the School database.</span></span> <span data-ttu-id="36931-107">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="36931-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="36931-108">Okul modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36931-108">Generate the School model.</span></span> <span data-ttu-id="36931-109">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="36931-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="36931-110">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="36931-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36931-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36931-111">See Also</span></span>  
 [<span data-ttu-id="36931-112">Nasıl yapılır: bir Entity Framework projesi el ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36931-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="36931-113">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="36931-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="36931-114">Nasıl yapılır: sorgu performansını artırmak için görünümlerini önceden oluşturmak</span><span class="sxs-lookup"><span data-stu-id="36931-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="36931-115">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36931-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
