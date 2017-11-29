---
title: "Nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4abb20ca2ff26fa4e2105bae87274028592aa510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="8e94f-102">Nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanın</span><span class="sxs-lookup"><span data-stu-id="8e94f-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="8e94f-103">Bu konuda nasıl kullanılacağını gösterir [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) .csdl dosya tabanlı bir nesne katmanı kodu oluşturmak için araç.</span><span class="sxs-lookup"><span data-stu-id="8e94f-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="8e94f-104">Nesne katman kodunu EdmGen.exe kullanarak bir Visual Basic proje Okul modeli oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8e94f-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="8e94f-105">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8e94f-105">Create the School database.</span></span> <span data-ttu-id="8e94f-106">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="8e94f-106">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="8e94f-107">Okul model oluşturmak veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="8e94f-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="8e94f-108">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="8e94f-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="8e94f-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="8e94f-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="8e94f-110">Nesne katman kodunu EdmGen.exe kullanarak bir C# projesi için Okul modeli oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8e94f-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="8e94f-111">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8e94f-111">Create the School database.</span></span> <span data-ttu-id="8e94f-112">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="8e94f-112">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="8e94f-113">Okul model oluşturmak veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="8e94f-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="8e94f-114">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="8e94f-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="8e94f-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="8e94f-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e94f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e94f-116">See Also</span></span>  
 [<span data-ttu-id="8e94f-117">Modelleme ve eşleme</span><span class="sxs-lookup"><span data-stu-id="8e94f-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="8e94f-118">Nasıl yapılır: bir Entity Framework projesi el ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e94f-118">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="8e94f-119">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="8e94f-119">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="8e94f-120">Nasıl yapılır: sorgu performansını artırmak için görünümlerini önceden oluşturmak</span><span class="sxs-lookup"><span data-stu-id="8e94f-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="8e94f-121">Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları oluşturmak için kullanın</span><span class="sxs-lookup"><span data-stu-id="8e94f-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
