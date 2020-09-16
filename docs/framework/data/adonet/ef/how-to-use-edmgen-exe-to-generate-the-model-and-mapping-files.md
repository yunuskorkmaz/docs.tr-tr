---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 6b41ce971f14938c7bb04a174dbf6029c564c788
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546582"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma
Bu konu, okul veritabanına bağlı olarak aşağıdaki dosyaları oluşturmak için EDM Oluşturucu (EdmGen.exe) aracının nasıl kullanılacağını gösterir:  
  
- Kavramsal bir model (. csdl dosyası).  
  
- Depolama modeli (. ssdl dosyası).  
  
- Kavramsal ve depolama modelleri (bir. msl dosyası) arasında eşleme.  
  
- Visual Basic veya C# ' deki nesne katmanı kodu.  
  
- Dosyaları görüntüleyin.  
  
 EdmGen.exe Aracı, yukarıda listelenen dosyaları oluşturmak için/Mode: FullGeneration kullanır. EdmGen.exe komutları hakkında daha fazla bilgi için bkz. [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanıyorsanız, yine de Visual Studio projenizi Entity Framework kullanacak şekilde yapılandırmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: el ile Entity Framework projesi yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> EdmGen.exe tarafından oluşturulan kavramsal bir model, veritabanındaki tüm nesneleri içerir. Yalnızca belirli nesneleri içeren kavramsal bir model oluşturmak istiyorsanız Varlık Veri Modeli Sihirbazı ' nı kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe kullanarak bir Visual Basic projesi için okul modeli oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe kullanarak bir C# projesi için okul modeli oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
