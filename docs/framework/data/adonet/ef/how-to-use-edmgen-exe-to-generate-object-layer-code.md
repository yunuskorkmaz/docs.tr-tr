---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: b85bacff093c268cd35dca2ede36e6ceb74ca4d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251399"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="b6d8f-102">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6d8f-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="b6d8f-103">Bu konu,. csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Oluşturucu (EdmGen. exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="b6d8f-104">EdmGen. exe kullanarak bir Visual Basic projesi için okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b6d8f-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="b6d8f-105">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-105">Create the School database.</span></span> <span data-ttu-id="b6d8f-106">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b6d8f-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b6d8f-107">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="b6d8f-108">Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="b6d8f-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="b6d8f-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="b6d8f-110">EdmGen. exe kullanarak bir C# projenin okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b6d8f-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="b6d8f-111">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-111">Create the School database.</span></span> <span data-ttu-id="b6d8f-112">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b6d8f-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b6d8f-113">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="b6d8f-114">Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="b6d8f-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="b6d8f-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b6d8f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-116">See also</span></span>

- [<span data-ttu-id="b6d8f-117">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="b6d8f-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="b6d8f-118">[Nasıl yapılır: Entity Framework projesini el ile yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6d8f-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="b6d8f-119">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6d8f-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="b6d8f-120">[Nasıl yapılır: Sorgu performansını artırmak için görünümleri önceden oluşturun](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6d8f-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="b6d8f-121">Nasıl yapılır: Modeli ve eşleme dosyalarını oluşturmak için EdmGen. exe kullanma</span><span class="sxs-lookup"><span data-stu-id="b6d8f-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
