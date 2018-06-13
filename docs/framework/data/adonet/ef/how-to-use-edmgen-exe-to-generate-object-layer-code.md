---
title: 'Nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanın'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: cd919f382096af6ff3e5e27225619767f3922ff0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761096"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="119ed-102">Nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanın</span><span class="sxs-lookup"><span data-stu-id="119ed-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="119ed-103">Bu konuda nasıl kullanılacağını gösterir [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) .csdl dosya tabanlı bir nesne katmanı kodu oluşturmak için araç.</span><span class="sxs-lookup"><span data-stu-id="119ed-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="119ed-104">Nesne katman kodunu EdmGen.exe kullanarak bir Visual Basic proje Okul modeli oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="119ed-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="119ed-105">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="119ed-105">Create the School database.</span></span> <span data-ttu-id="119ed-106">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="119ed-106">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="119ed-107">Okul model oluşturmak veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="119ed-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="119ed-108">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="119ed-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="119ed-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="119ed-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="119ed-110">Nesne katman kodunu EdmGen.exe kullanarak bir C# projesi için Okul modeli oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="119ed-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="119ed-111">Okul veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="119ed-111">Create the School database.</span></span> <span data-ttu-id="119ed-112">Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="119ed-112">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="119ed-113">Okul model oluşturmak veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="119ed-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="119ed-114">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="119ed-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="119ed-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="119ed-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="119ed-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="119ed-116">See Also</span></span>  
 [<span data-ttu-id="119ed-117">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="119ed-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="119ed-118">Nasıl yapılır: bir Entity Framework projesi el ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="119ed-118">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="119ed-119">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="119ed-119">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="119ed-120">Nasıl yapılır: sorgu performansını artırmak için görünümlerini önceden oluşturmak</span><span class="sxs-lookup"><span data-stu-id="119ed-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="119ed-121">Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="119ed-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
