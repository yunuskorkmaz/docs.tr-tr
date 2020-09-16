---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9a73a803d310ebd847e49f4bd71609f8ef9f2944
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546646"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="a388b-102">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a388b-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="a388b-103">Bu konu,. csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a388b-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="a388b-104">EdmGen.exe kullanarak bir Visual Basic projesi için okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a388b-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="a388b-105">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a388b-105">Create the School database.</span></span> <span data-ttu-id="a388b-106">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a388b-106">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a388b-107">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="a388b-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a388b-108">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="a388b-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="a388b-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="a388b-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="a388b-110">EdmGen.exe kullanarak bir C# projesi için okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a388b-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="a388b-111">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a388b-111">Create the School database.</span></span> <span data-ttu-id="a388b-112">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a388b-112">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a388b-113">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="a388b-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a388b-114">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="a388b-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="a388b-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="a388b-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a388b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a388b-116">See also</span></span>

- [<span data-ttu-id="a388b-117">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="a388b-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="a388b-118">[Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a388b-118">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="a388b-119">[ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a388b-119">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="a388b-120">[Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a388b-120">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="a388b-121">Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a388b-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
