---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150564"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="a3586-102">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3586-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="a3586-103">Bu konu, .csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3586-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="a3586-104">EdmGen.exe kullanarak Visual Basic projesi için Okul modeli için nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a3586-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="a3586-105">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3586-105">Create the School database.</span></span> <span data-ttu-id="a3586-106">Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3586-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a3586-107">Okul modelini oluşturun veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="a3586-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a3586-108">Daha fazla bilgi için [bkz: Modeli oluşturmak ve Dosyaları Eşleme için EdmGen.exe'yi kullanın.](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)</span><span class="sxs-lookup"><span data-stu-id="a3586-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="a3586-109">Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:</span><span class="sxs-lookup"><span data-stu-id="a3586-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="a3586-110">EdmGen.exe kullanarak c# projesi için Okul modeli için nesne katmanı kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a3586-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="a3586-111">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3586-111">Create the School database.</span></span> <span data-ttu-id="a3586-112">Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3586-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a3586-113">Okul modelini oluşturun veya School.csdl dosyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="a3586-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="a3586-114">Daha fazla bilgi için [bkz: Modeli oluşturmak ve Dosyaları Eşleme için EdmGen.exe'yi kullanın.](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)</span><span class="sxs-lookup"><span data-stu-id="a3586-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="a3586-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:</span><span class="sxs-lookup"><span data-stu-id="a3586-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3586-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3586-116">See also</span></span>

- [<span data-ttu-id="a3586-117">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="a3586-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="a3586-118">[Nasıl?](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3586-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="a3586-119">[ADO.NET Varlık Veri Modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3586-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="a3586-120">[Nasıl yapilir: Sorgu Performansını Artırmak için Görünümleri Önceden Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3586-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="a3586-121">Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3586-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
