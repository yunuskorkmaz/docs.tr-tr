---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: model ve eşleme dosyalarını doğrulamak için EdmGen.exe kullanma'
title: 'Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: e729ea36b7ff17dc318f4488a669b968161aea8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697354"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="06f53-103">Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="06f53-103">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>

<span data-ttu-id="06f53-104">Bu konuda, bir [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md) aracının model ve eşleme dosyalarını doğrulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06f53-104">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="06f53-105">Daha fazla bilgi için bkz. [varlık veri modeli](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="06f53-105">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="06f53-106">EdmGen.exe kullanarak okul modelini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="06f53-106">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="06f53-107">Okul veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06f53-107">Create the School database.</span></span> <span data-ttu-id="06f53-108">Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="06f53-108">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="06f53-109">Okul modelini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06f53-109">Generate the School model.</span></span> <span data-ttu-id="06f53-110">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="06f53-110">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="06f53-111">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="06f53-111">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="06f53-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06f53-112">See also</span></span>

- <span data-ttu-id="06f53-113">[Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06f53-113">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="06f53-114">[ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06f53-114">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="06f53-115">[Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06f53-115">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="06f53-116">Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06f53-116">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
