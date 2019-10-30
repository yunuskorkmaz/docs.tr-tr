---
title: 'Nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyalarını oluşturma'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: c74f9344891d43f21034a48ac51723fa7441744d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040304"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyalarını oluşturma
Bu konu, okul veritabanına bağlı olarak aşağıdaki dosyaları oluşturmak için EDM Oluşturucu (EdmGen. exe) aracının nasıl kullanılacağını gösterir:  
  
- Kavramsal bir model (. csdl dosyası).  
  
- Depolama modeli (. ssdl dosyası).  
  
- Kavramsal ve depolama modelleri (bir. msl dosyası) arasında eşleme.  
  
- Visual Basic veya C#içindeki nesne katmanı kodu.  
  
- Dosyaları görüntüleyin.  
  
 EdmGen. exe aracı, yukarıda listelenen dosyaları oluşturmak için/Mode: FullGeneration kullanır. EdmGen. exe komutları hakkında daha fazla bilgi için bkz. [EDM Oluşturucu (EdmGen. exe)](edm-generator-edmgen-exe.md).  
  
 Modeli ve eşleme dosyalarını oluşturmak için EdmGen. exe ' yi kullanırsanız, Visual Studio projenizi Entity Framework kullanmak için yine de yapılandırmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: el ile Entity Framework projesi yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> EdmGen. exe tarafından oluşturulan kavramsal bir model, veritabanındaki tüm nesneleri içerir. Yalnızca belirli nesneleri içeren kavramsal bir model oluşturmak istiyorsanız Varlık Veri Modeli Sihirbazı ' nı kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen. exe kullanarak bir Visual Basic projesi için okul modeli oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen. exe kullanarak bir C# proje için okul modeli oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
