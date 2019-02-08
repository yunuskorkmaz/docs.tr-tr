---
title: "Nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın"
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 49890eb8bdb9f956cc36b3adde2f11db1e1e07bc
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826960"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın
Bu konuda EDM Oluşturucu (EdmGen.exe) aracı School veritabanını temel alan aşağıdaki dosyaları oluşturmak için nasıl kullanılacağını gösterir:  
  
-   Kavramsal model (.csdl dosyası).  
  
-   Bir depolama model (.ssdl dosyası).  
  
-   Kavramsal ve depolama modelleri (.msl dosyası) arasında eşleme.  
  
-   Visual Basic veya C# içinde nesne katmanı kodu.  
  
-   Dosyaları görüntüleyin.  
  
 EdmGen.exe aracı /mode:FullGeneration yukarıda listelenen dosyaları oluşturmak için kullanır. EdmGen.exe komutlar hakkında daha fazla bilgi için bkz. [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanırsanız, Visual Studio projenizi kullanmak üzere yapılandırmak yine [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: El ile bir Entity Framework projesinin yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
>  EdmGen.exe tarafından oluşturulan bir kavramsal model veritabanındaki tüm nesneleri içerir. Yalnızca belirli nesne içeren bir kavramsal model oluşturmak istiyorsanız, varlık veri modeli Sihirbazı kullanın. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe kullanarak bir Visual Basic projesi için Okul modeli oluşturmak için  
  
1.  School veritabanını oluşturun. Daha fazla bilgi için [School örnek veritabanını oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2.  Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Okul modelini EdmGen.exe kullanarak bir C# projesi oluşturmak için  
  
1.  School veritabanını oluşturun. Daha fazla bilgi için [School örnek veritabanını oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2.  Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Modelleme ve Eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Nasıl yapılır: El ile bir Entity Framework projesinin yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Nasıl yapılır: Sorgu performansını artırmak için görünümleri önceden oluştur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: Model ve eşleme dosyalarını doğrulama için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
