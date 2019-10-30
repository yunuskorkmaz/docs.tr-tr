---
title: 'Nasıl yapılır: EdmGen. exe kullanarak nesne katmanı kodu oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9182f815a502488f955f64f6c19aad7865d0c7c6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039978"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="d2a0a-102">Nasıl yapılır: EdmGen. exe kullanarak nesne katmanı kodu oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2a0a-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="d2a0a-103">Bu konu,. csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Oluşturucu (EdmGen. exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="d2a0a-104">EdmGen. exe kullanarak bir Visual Basic projesi için okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2a0a-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d2a0a-105">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-105">Create the School database.</span></span> <span data-ttu-id="d2a0a-106">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d2a0a-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d2a0a-107">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d2a0a-108">Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="d2a0a-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d2a0a-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d2a0a-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="d2a0a-110">EdmGen. exe kullanarak bir C# projenin okul modeline yönelik nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2a0a-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d2a0a-111">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-111">Create the School database.</span></span> <span data-ttu-id="d2a0a-112">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d2a0a-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d2a0a-113">Okul modelini oluşturun veya okul. csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d2a0a-114">Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="d2a0a-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d2a0a-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d2a0a-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d2a0a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2a0a-116">See also</span></span>

- [<span data-ttu-id="d2a0a-117">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="d2a0a-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="d2a0a-118">[Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2a0a-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="d2a0a-119">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2a0a-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="d2a0a-120">[Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2a0a-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="d2a0a-121">Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2a0a-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
